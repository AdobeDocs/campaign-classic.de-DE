---
title: Protokollgenauigkeit
seo-title: Protokollgenauigkeit
description: Protokollgenauigkeit
seo-description: null
page-status-flag: never-activated
uuid: 8396bc4f-2954-40bb-b511-61802e60e123
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: c6c39b7d-7bbd-4789-b1ea-b938153e9679
translation-type: tm+mt
source-git-commit: 849e1ebf14f707d9e86c5a152de978acb6f1cb35
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 100%

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
   >Wenn Sie **trackingFilter:*** verwenden, werden alle Protokolltypen aktiviert: ncm, rdr, nms, jst, timing, wdbc, ldap, soap, xtk, xtkquery, session, xtkwriter, network, pop3, inmail\
   >Die nützlichsten Protokolltypen sind: **wdbc** (zeigt alle SQL-Abfragen an), **soap** (zeigt alle SOAP-Aufrufe an), **ldap** (zeigt alle LDAP-Abfragen nach der Authentifizierung an), **xtkquery** (zeigt die Liste aller Abfragedef an).\
   >Sie können sie einzeln verwenden (**z. B. trackFilter:soap,wdbc** ). Sie können sie auch alle aktivieren und bestimmte andere ausschließen: **-tracefilter:*,!soap**

   Vergewissern Sie sich, dass der Fehler tatsächlich aufgetreten ist, und starten Sie den Prozess auf die normale Weise neu:

   ```
   nlserver restart <MODULE_NAME> -noconsole
   ```

>[!IMPORTANT]
>
>Die Protokolle dieser Befehle werden in der Protokolldatei des Moduls gespeichert.

Hier ist ein Beispiel speziell für das Webmodul. Die anderen Module funktionieren wie oben angegeben.

Vergewissern Sie sich vor dem Senden dieses Befehls, dass kein in Verarbeitung befindlicher Auftrag betroffen ist.

```
nlserver pdump -who
```

Fahren Sie anschließend das Modul herunter und starten Sie es im **TraceFilter** -Modus neu.

```
nlserver stop web; LD_PRELOAD=libjsig.so nlserver web -tomcat -verbose -tracefilter:* -tracefile:web_debug@default
```

Ein weiteres Beispiel:

```
nlserver stop mta@<INSTANCE_NAME>; nlserver mta -instance:<INSTANCE_NAME> -tracefilter:* -tracefile:mta_debug@<INSTANCE_NAME>
```

>[!NOTE]
>
>Im **Tracefile** -Modus können Sie die Protokolle speichern. In den obigen Beispielen werden die Protokolle in den Dateien **var/`<instance-name>`/mta_debug.log** und **var/default/web_debug.log** gespeichert.

>[!IMPORTANT]
>
>Fügen Sie unter Windows nicht die Option LD_PRELOAD hinzu. Der folgende Befehl reicht aus:\
>nlserver web -tomcat -verbose -tracefilter:*

Vergewissern Sie sich, dass das Problem erneut auftritt, und starten Sie dann das Modul neu:

```
nlserver restart web -tomcat -noconsole
```

Alle Informationen finden Sie in der Datei **/usr/local/neolane/nl6/var/default/log/web.log**.
