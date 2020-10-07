---
title: Stack Trace in Linux
seo-title: Stack Trace in Linux
description: Stack Trace in Linux
seo-description: null
page-status-flag: never-activated
uuid: d839df47-902f-4b92-bc78-536fc4fb6c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: 60f306ea-4593-4e56-896e-8933277ee26a
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 14%

---


# Stack Trace in Linux{#stack-trace-in-linux}

Eine **Stapelablaufverfolgung** stellt eine in einer **Core** -Typdatei enthaltene Ablaufverfolgung dar. Diese Datei wird im Ereignis eines Computerfehlers generiert. Sie kann die Herkunft des Fehlers identifizieren.

>[!NOTE]
>
>* Eine **Core** -Datei heißt **core.`<num>`**.
>* **gdb - Der GNU-Debugger** muss auf dem Computer installiert sein.

>



Adobe Campaign Technical Support kann Sie nach dieser **Stapelablaufverfolgung** fragen. Geben Sie zum Abrufen folgende Befehle in Linux ein:

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

Adobe Campaign Technical Support bittet Sie, diesen Befehl mit einer bestimmten ausführbaren Datei auszuführen (die von uns bereitgestellt wird).

Führen Sie in diesem Fall einfach den folgenden Befehl aus, indem Sie **nlserver** durch die ausführbare Datei ersetzen, die von Adobe Campaign bereitgestellt wird:

```
gdb nlserver <coreFile>
```

Beispiel:

```
gdb nlserver.1823 <coreFile>
```

