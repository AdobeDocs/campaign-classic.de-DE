---
product: campaign
title: Protokollgenauigkeit
description: Protokollgenauigkeit
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: c2470098-62f3-4fee-b1c5-800ed0e91f75
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 79%

---

# Protokollgenauigkeit{#log-precision}



Sie können diesen Vorgang auf alle Adobe Campaign-Module anwenden, um die Protokollgenauigkeit zu erhöhen.

Es umfasst den Neustart der Prozesse mit einer höheren Protokollierungsstufe.

>[!IMPORTANT]
>
>Durch diesen Vorgang werden die in diesem Modul ausgeführten Dienste abgebrochen.

Adobe Campaign kann mit zwei Protokollierungsstufen betrieben werden:

1. Der Modus **Verbose** ist die erste Ebene nach der Standardstufe. Der folgende Befehl aktiviert ihn:

   ```
   nlserver restart <MODULE_NAME> -verbose 
   ```

   Vergewissern Sie sich, dass der Fehler tatsächlich aufgetreten ist, und starten Sie den Prozess auf die normale Weise neu:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

1. Der **TraceFilter** -Modus, mit dem Sie die größte Anzahl von Protokollen speichern können. Sie wird durch den folgenden Befehl aktiviert:

   ```
   nlserver stop <MODULE_NAME>; nlserver <MODULE_NAME> -verbose -tracefilter:*
   ```

   >[!NOTE]
   >
   >Wenn Sie **trackingFilter:&#42;** verwenden, werden alle Protokolltypen aktiviert: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   Die nützlichsten Protokolltypen sind: **wdbc** (zeigt alle SQL-Abfragen an), **soap** (zeigt alle SOAP-Aufrufe an), **ldap** (zeigt alle LDAP-Abfragen nach der Authentifizierung an), **xtkquery** (zeigt die Liste aller Abfragedef an).\
   Sie können sie einzeln verwenden (**z. B. trackFilter:soap,wdbc** ). Sie können auch alle aktivieren und bestimmte andere ausschließen: **-tracefilter:&#42;,!soap**

   Vergewissern Sie sich, dass der Fehler tatsächlich aufgetreten ist, und starten Sie den Prozess auf die normale Weise neu:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
Die Protokolle dieser Befehle werden in der Protokolldatei des Moduls gespeichert.

Hier ist ein Beispiel speziell für das Webmodul. Die anderen Module funktionieren wie oben angegeben.

Vergewissern Sie sich vor dem Senden dieses Befehls, dass kein laufender Auftrag betroffen ist:

```
nlserver pdump -who
```

Fahren Sie anschließend das Modul herunter und starten Sie es im Modus **TraceFilter** neu:

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Ein weiteres Beispiel:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
Im **Tracefile** -Modus können Sie die Protokolle speichern. In den obigen Beispielen werden die Protokolle in den Dateien **var/`<instance-name>`/mta_debug.log** und **var/default/web_debug.log** gespeichert.

>[!IMPORTANT]
>
Fügen Sie unter Windows nicht die Option LD_PRELOAD hinzu. Der folgende Befehl reicht aus:\
nlserver web -tomcat -verbose -tracefilter:&#42;

Vergewissern Sie sich, dass das Problem erneut auftritt, und starten Sie dann das Modul neu:

```
nlserver restart web -tomcat -noconsole
```

Alle Informationen finden Sie in der Datei **/usr/local/neolane/nl6/var/default/log/web.log**.
