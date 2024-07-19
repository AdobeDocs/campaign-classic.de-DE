---
product: campaign
title: Stack Trace in Linux
description: Stack Trace in Linux
feature: Monitoring
badge-v7-prem: label="Nur On-Premise/Hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=de" tooltip="Gilt nur für Hybrid- und On-Premise-Bereitstellungen"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: 91662d6d-2177-4440-b31f-7b031bd953cb
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 19%

---

# Stack Trace in Linux{#stack-trace-in-linux}



Ein **Stacktrace** steht für eine Spur, die in einer Datei vom Typ **core** enthalten ist. Diese Datei wird im Falle eines Maschinenfehlers generiert. Sie kann die Herkunft des Fehlers identifizieren.

>[!NOTE]
>
>* Eine **core** -Datei heißt **core.`<num>`**.
>* **gdb - Der GNU-Debugger** muss auf dem Computer installiert sein.
>

Der technische Support von Adobe Campaign kann Sie nach diesem **Stacktrace** fragen. Geben Sie zum Abrufen die folgenden Befehle in Linux ein:

```
su - neolane
gdb nlserver <coreFile>
//You get lots of output but the stack trace (or Back trace) can be obtained with : 
(gdb) bt
// and forward all the output : 
#0 0x0836c189 in ObjectValue::SetPropertyTarget ()
#1 0x082623b3 in CXtkScriptProperty::VDeclareProperties ()
#2 0x0826a835 in CXtkScriptContext::OnGetProperty ()
#3 0x08370b3d in JavaScriptGetProperty ()
#4 0x557b8aa7 in js_Interpret () from /usr/local/neolane/nl6/lib/libmozjs.so
#5 0x557afb97 in js_Execute () from /usr/local/neolane/nl6/lib/libmozjs.so
#6 0x5578921f in JS_ExecuteScript () from /usr/local/neolane/nl6/lib/libmozjs.so
#7 0x08370468 in JavaScriptSource::Evaluate ()
#8 0x0848fa03 in JSTDeliveryContext::ProcessScript ()
#9 0x0848fcb6 in JSTDeliveryContext::ProcessTemplate ()
#10 0x08460d2b in CDeliveryToolbox::CreateMailMessage ()
#11 0x080d51fe in CMtaQueue::PrepareMessages ()
#12 0x080d2b07 in CMtaQueue::Prepare ()
#13 0x080dca38 in CMtaChild::OnRun ()
#14 0x0814792c in ThreadStartRoutine ()
#15 0x55575b63 in start_thread () from /lib/tls/libpthread.so.0
#16 0x5565918a in clone () from /lib/tls/libc.so.6
```

Der technische Support von Adobe Campaign kann Sie bitten, diesen Befehl mit einer bestimmten ausführbaren Datei auszuführen (die von uns bereitgestellt wird).

Führen Sie in diesem Fall einfach den folgenden Befehl aus, indem Sie **nlserver** durch die von Adobe Campaign bereitgestellte ausführbare Datei ersetzen:

```
gdb nlserver <coreFile>
```

Beispiel:

```
gdb nlserver.1823 <coreFile>
```
