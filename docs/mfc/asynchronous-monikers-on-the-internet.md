---
title: Asynchronní Monikery na Internetu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb9828734985c25996e7e2d1a6f390a0b629d998
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-monikers-on-the-internet"></a>Asynchronní monikery na Internetu
Internetu vyžaduje nové přístupy k návrhu aplikace z důvodu jeho přístup k pomalé síti. Aplikace by měla provést přístup k síti asynchronně, aby se zabránilo zablokování uživatelského rozhraní. Třída knihovny MFC [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) poskytuje asynchronní podpora pro stahování souborů.  
  
 Pomocí asynchronní monikery můžete rozšířit aplikace modelu COM stáhnout asynchronně přes Internet a poskytnout progresivní vykreslování rozsáhlé objekty, jako je například rastrové obrázky a VRML objektů. Asynchronní monikery povolit ve vlastnosti ovládacího prvku ActiveX nebo soubor na Internetu ke stažení bez blokování odezvy uživatelského rozhraní.  
  
## <a name="advantages-of-asynchronous-monikers"></a>Výhody asynchronní Monikery  
 Můžete použít asynchronní monikery na:  
  
-   Stáhněte si kód a soubory bez blokování.  
  
-   Stáhněte si vlastnosti v ovládacích prvcích ActiveX bez blokování.  
  
-   Přijímání oznámení o průběhu stahování.  
  
-   Sledovat průběh a informace o stavu Připraveno.  
  
-   Poskytnout informace o stavu uživatele o průběhu.  
  
-   Povolí uživateli stahování kdykoli zrušit.  
  
## <a name="mfc-classes-for-asynchronous-monikers"></a>MFC – třídy pro asynchronní Monikery  
 [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md) je odvozený od [CMonikerFile](../mfc/reference/cmonikerfile-class.md), který je zase odvozen z [COleStreamFile](../mfc/reference/colestreamfile-class.md). A `COleStreamFile` objekt představuje a datový proud; `CMonikerFile` objektu používá `IMoniker` k získání dat a a `CAsyncMonikerFile` objekt nemá tak asynchronně.  
  
 Asynchronní monikery se používají primárně v internetových aplikací a ovládací prvky ActiveX poskytnout reagující uživatelské rozhraní během přenosu souborů. Typickým příkladem toho je použití [CDataPathProperty](../mfc/reference/cdatapathproperty-class.md) zajistit asynchronní vlastnosti pro ovládací prvky ActiveX.  
  
## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>MFC – třídy pro cesty k datům v ovládacích prvcích ActiveX  
 Třídy MFC `CDataPathProperty` a [CCachedDataPathProperty](../mfc/reference/ccacheddatapathproperty-class.md) implementovat vlastnosti ovládacích prvků ActiveX, které je možné načíst asynchronně. Po spuštění synchronní jsou načteny asynchronní vlastnosti. Asynchronní ovládací prvky ActiveX opakovaně vyvolání zpětného volání k označení dostupnost nových dat systému exchange během zdlouhavé vlastnost.  
  
 `CDataPathProperty` je odvozený od `CAsyncMonikerFile`. `CCachedDataPathProperty` je odvozený od `CDataPathProperty`. Pokud chcete implementovat asynchronní vlastnosti v vaše ovládací prvky ActiveX, odvození třídy z `CDataPathProperty` nebo `CCachedDataPathProperty`a přepsat [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a další oznámení, je třeba přijmout.  
  
#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Chcete-li stáhnout soubor pomocí asynchronní monikery  
  
1.  Deklarace třídy odvozené od [CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md).  
  
2.  Přepsání [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a zobrazí data.  
  
3.  Přepsání dalších členské funkce, včetně [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), a [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).  
  
4.  Deklarujte instanci této třídy a použít ho k otevírání adres URL.  
  
 Informace o stahování asynchronně v ovládacím prvku ActiveX najdete v tématu [ActiveX – ovládací prvky na Internetu](../mfc/activex-controls-on-the-internet.md).  
  
## <a name="see-also"></a>Viz také  
 [Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

