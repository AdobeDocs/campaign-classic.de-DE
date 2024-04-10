---
product: campaign
title: Integrieren des Campaign SDK
description: Erfahren Sie, wie Sie das Campaign SDK in Ihre Mobile App integrieren können.
badge-v7-only: label="v7" type="Informative" tooltip="Gilt nur für Campaign Classic v7"
feature: Mobile SDK Integration, Push
role: User, Developer
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 87%

---

# Integrieren des Campaign SDK in Ihre App {#integrating-campaign-sdk-into-the-mobile-application}



>[!CAUTION]
>
>Adobe empfiehlt dringend, das Adobe Experience Platform Mobile SDK zu verwenden, indem die Adobe Campaign-Erweiterung in der Benutzeroberfläche „Datenerfassung“ konfiguriert wird. Mit dem Adobe Experience Platform Mobile SDK können Sie die Experience Cloud-Lösungen und -Dienste von Adobe in Ihren mobilen Apps nutzen. Die SDK-Konfiguration wird über die Datenerfassungs-Benutzeroberfläche verwaltet, um eine flexible Konfiguration und erweiterbare, regelbasierte Integrationen zu ermöglichen. [Weitere Informationen finden Sie in der Dokumentation zu Adobe Developer](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

Um Campaign SDK (früher bekannt als Neolane SDK) zu erhalten, wenden Sie sich an die [Adobe Kundenunterstützung](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

Weitere Informationen zu den verschiedenen unterstützten Android- und iOS-Versionen finden Sie in der [Kompatibilitätsmatrix](../../rn/using/compatibility-matrix.md#MobileSDK).

Im Folgenden finden Sie die Integrationsschritte für das Campaign SDK.

+++**Laden von Campaign SDK**

* **Android**: erfordert die Verknüpfung der Datei **neolane_sdk-release.aar** mit dem Projekt.

  Folgende Erlaubnis ermöglicht den Zugriff auf den Adobe-Campaign-Server:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  Folgende Erlaubnis ermöglicht den Abruf einer eindeutigen Kennung für jedes Telefon:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  Ab der SDK-Version 1.0.24 wird diese Erlaubnis nur für Android-Versionen unter Android 6.0 verwendet.

  Ab der SDK-Version 1.0.26 wird diese Erlaubnis nicht mehr verwendet.

* **In iOS**: die **libNeolaneSDK.a** und **In: neolane_sdk.h** Dateien müssen mit dem Projekt verknüpft sein. Ab Version 1.0.24 des SDK wird die Option **ENABLE_BITCODE** ist aktiviert.

  >[!NOTE]
  >
  >Für die Version 1.0.25 des SDK sind die vier Architekturen in der Datei **Neolane_SDK.h** verfügbar.

+++

+++**Deklarieren der Integrationseinstellungen**

Zur Integration des Campaign SDK in die Mobile App benötigt der Entwickler folgende Informationen vom funktionalen Administrator:

* **Integrationsschlüssel**: zur Identifizierung der Mobile App durch die Adobe-Campaign-Plattform.

  >[!NOTE]
  >
  >Der Integrationsschlüssel ist in der Adobe Campaign-Konsole im Tab **[!UICONTROL Informationen]** des dedizierten Dienstes der Mobile App angegeben. Weitere Informationen finden Sie unter [Konfiguration einer Mobile App in Adobe Campaign](configuring-the-mobile-application.md).

* **Tracking-URL**: entspricht der Adresse des Adobe-Campaign-Trackingservers.
* **Marketing-URL**: um die Sammlung der Abonnements zu ermöglichen.

* **Für Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **Für iOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**Registrierungsfunktion**

Die Registrierungsfunktion ermöglicht

* das Senden der Benachrichtigungskennung oder Push-ID (deviceToken bei iOS und registrationID bei Android) an Adobe Campaign.
* die Abfrage des Abstimmschlüssels oder userKey (z. B. E-Mail-Adresse oder Kundennummer).

* **Für Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  Wenn Sie FCM (Firebase Cloud Messaging) verwenden, empfehlen wir Ihnen, beim Aufruf der **onTokenRefresh**-Funktion die **registerDevice**-Funktion zu verwenden, um Adobe Campaign vom Wechsel des Mobilgeräte-Tokens des Nutzers in Kenntnis zu setzen.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **Für iOS**:

  ```
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

+++

+++**Tracking-Funktion**

* **Für Android**:

  Trackingfunktionen ermöglichen das Tracking der Benachrichtigungsanzeige (Impression) und die Aktivierung der Benachrichtigungen (Öffnungen).

  So verfolgen Sie die Anzeige der Benachrichtigung (erfolgt durch Aufruf der **notifyReceive** Funktion des SDK), folgen Sie der unten stehenden Implementierung. Beachten Sie, dass wir Ihnen bei Verwendung von FCM (Firebase Cloud Messaging) empfehlen, **notifyReceive** -Funktion verwenden, wenn die **onMessageReceived** -Funktion wird vom Android-System aufgerufen.

  ```
  package com.android.YourApplication;
  
  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;
  
  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;
  
  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;
  
  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";
  
    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }
  
      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;
  
    // notify Neolane that a notification just arrived
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
    NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
    nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1){}
    });
    if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;
  
        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
  
        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();
  
        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Im Folgenden finden Sie ein Implementierungsbeispiel für das Tracking einer geöffneten Benachrichtigung (ausgeführt durch Aufruf der **notifyOpening** Funktion des SDK). Die **Benachrichtigungsaktivität** Klasse entspricht der Klasse, die zum Erstellen des **notifIntent** -Objekt im vorherigen Beispiel.

  ```
  public class NotificationActivity extends Activity {
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
    }
   }
  }
  ```

* **Für iOS**:

  Mithilfe der Trackingfunktion lässt sich die Aktivierung der Benachrichtigungen (Öffnungen) verfolgen.

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >Ab Version 7.0 gilt Folgendes: **`application:didReceiveRemoteNotification:fetchCompletionHandler`** ist implementiert, ruft das Betriebssystem nur diese Funktion auf. Die **`application:didReceiveRemoteNotification`** Die Funktion wird daher nicht aufgerufen.

+++

+++**Tracking von stillen Benachrichtigungen**

Unter iOS können Sie stille Benachrichtigungen senden. Das sind Benachrichtigungen oder Daten, die direkt an eine mobile App gesendet werden, ohne Hinweise zu erzeugen. Adobe Campaign ermöglicht das Tracken dieser Benachrichtigungen.

Um stille Benachrichtigungen zu tracken, gehen Sie analog zum folgenden Beispiel vor:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

+++

+++**Delegation von RegisterDeviceStatus**

>[!NOTE]
>
>Bitte beachten Sie, dass diese Funktion nur für iOS verfügbar ist.

Mit dem Delegationsprotokoll können Sie in iOS das Ergebnis des **registerDevice**-Aufrufs abrufen und feststellen, ob bei der Registrierung ein Fehler aufgetreten ist.

Der **registerDeviceStatus**-Prototyp ist:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Status** ermöglicht festzustellen, ob eine Registrierung erfolgreich war oder ob ein Fehler aufgetreten ist.

**ErrorReason** liefert zusätzliche Informationen zu den aufgetretenen Fehlern. Weiterführende Informationen zu möglichen Fehlern und deren Beschreibung finden Sie in der folgenden Tabelle.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Beschreibung<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registrierung erfolgreich<br /> </td>
   <td> LEER<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> Der Host-Name des ACC-Marketing-Servers ist leer oder nicht definiert.<br /> </td>
   <td> LEER<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> Der Integrationsschlüssel ist leer oder nicht definiert.<br /> </td>
   <td> LEER<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> Verbindungsproblem mit ACC<br /> </td>
   <td> Weitere Informationen (in der Sprache des Betriebssystems)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> Die bereitgestellte UUID (Integrationsschlüssel) ist unbekannt.<br /> </td>
   <td> LEER<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> Unerwarteter Fehler an ACC-Server zurückgegeben.<br /> </td>
   <td> Die an ACC zurückgegebene Fehlermeldung.<br /> </td>
  </tr>
 </tbody>
</table>

Die Definition des **Neolane_SDKDelegate**-Protokolls und der **registerDeviceStatus**-Delegation ist wie folgt:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Um die **registerDeviceStatus**-Delegation zu implementieren, gehen Sie folgendermaßen vor:

1. Implementieren Sie **setDelegate** während der SDK-Initialisierung.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Fügen Sie das Protokoll zu **@interface** Ihrer Klasse hinzu.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Implementieren Sie die Delegation in **AppDelegate**.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

+++

+++**Variablen**

Mit den Variablen können Sie das Verhalten von Mobile Apps nach dem Erhalt einer Benachrichtigung festlegen. Diese Variablen müssen im Code der Mobile App und in der Adobe Campaign-Konsole auf dem Tab **[!UICONTROL Variablen]** im dedizierten Mobile-App-Dienst definiert werden (siehe [Konfiguration einer Mobile App in Adobe Campaign](configuring-the-mobile-application.md)). Im Folgenden finden Sie ein Beispiel für einen Code, mit dem eine Mobile App alle hinzugefügten Variablen in einer Benachrichtigung erfassen kann. In unserem Beispiel verwenden wir die Variable „VAR“.

* **Für Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **Für iOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }
  
  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>Adobe empfiehlt, kurze Namen für die Variablen zu verwenden, da die Größe der Benachrichtigungen für iOS und Android auf 4 Kilobyte begrenzt ist.

+++

+++**Erweiterung für den Benachrichtigungsdienst**

**Für iOS**

Die Medien müssen auf der Ebene der Benachrichtigungsdiensterweiterung heruntergeladen werden.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

+++

+++**Erweiterung für Benachrichtigungsinhalt**

**Für iOS**

Gehen Sie hier folgendermaßen vor:

* Ordnen Sie Ihre Inhaltserweiterung der von Adobe Campaign gesendeten Kategorie zu:

  Wenn Ihre Mobile App ein Bild anzeigen soll, können Sie in Adobe Campaign als Kategoriewert &quot;image&quot; wählen und in Ihrer Mobile App eine Benachrichtigungserweiterung mit dem mit &quot;image&quot; festgelegten Parameter **UNNotificationExtensionCategory** erstellen. Wenn die Push-Benachrichtigung auf dem Gerät empfangen wird, wird die Erweiterung entsprechend dem definierten Kategoriewert abgerufen.

* Definieren Sie das Layout Ihrer Benachrichtigung.

  Sie müssen ein Layout mit den entsprechenden Widgets definieren.  Für ein Bild trägt das Widget den Namen **UIImageView**.

* Stellen Sie Ihre Medien dar.

  Sie müssen entsprechenden Code hinzufügen, um die Mediendaten an das Widget zu übertragen. Hier ist ein Beispiel für den Code eines Bildes:

  ```
  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>
  
  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end
  
  @implementation NotificationViewController
  
  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }
  
  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  ```

+++
