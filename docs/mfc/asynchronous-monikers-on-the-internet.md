---
title: Asynchronní monikery na Internetu
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX controls [MFC], asynchronous
- MFC, asynchronous monikers
- asynchronous monikers [MFC]
- Web applications [MFC], asynchronous
- downloading Internet resources and asynchronous monikers
- optimization [MFC], asynchronous downloading across Internet
- Internet [MFC], asynchronous downloading
ms.assetid: 418b0c64-0046-4dae-8118-c9c762b5822e
ms.openlocfilehash: 63bdc8372223075804d8c710909909382167b2c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591292"
---
# <a name="asynchronous-monikers-on-the-internet"></a>Asynchronní monikery na Internetu

Internetu vyžaduje nové přístupy k návrhu aplikace z důvodu jeho přístup k pomalé síti. Aplikace by měl provádět přístup k síti asynchronně, aby se zabránilo zablokování uživatelského rozhraní. Třída knihovny MFC [casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md) poskytuje asynchronní podporu pro stahování souborů.

S asynchronní monikery můžete rozšířit aplikace modelu COM asynchronně stahujete z Internetu a poskytnout progresivní vykreslování velké objekty, jako je například rastrové obrázky a VRML objektů. Asynchronní monikery povolit vlastnosti ovládacího prvku ActiveX nebo soubor na Internetu, aby bylo možné stáhnout bez blokování odezvy uživatelského rozhraní.

## <a name="advantages-of-asynchronous-monikers"></a>Výhody asynchronní Monikery

Asynchronní monikery můžete použít:

- Stáhněte si kód a soubory bez blokování.

- Stáhněte si vlastnosti v ovládacích prvcích ActiveX bez blokování.

- Přijímání oznámení o průběhu stahování.

- Sledování průběhu a informace o připraveném stavu.

- Zadejte informace o stavu uživatele o průběhu.

- Povolí uživateli stahování kdykoli zrušit.

## <a name="mfc-classes-for-asynchronous-monikers"></a>MFC – třídy pro asynchronní Monikery

[Casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md) je odvozen z [cmonikerfile –](../mfc/reference/cmonikerfile-class.md), který je zase odvozen z [colestreamfile –](../mfc/reference/colestreamfile-class.md). A `COleStreamFile` představuje objekt a datový proud; `CMonikerFile` objektu používá `IMoniker` na získání dat a `CAsyncMonikerFile` objekt provádí asynchronně.

Asynchronní monikery se používají především v internetových aplikací a ovládací prvky ActiveX k zajištění responzivní uživatelské rozhraní během přenosu souborů. Typickým příkladem tohoto je použití [cdatapathproperty –](../mfc/reference/cdatapathproperty-class.md) k poskytování asynchronní vlastností pro ovládací prvky ActiveX.

## <a name="mfc-classes-for-data-paths-in-activex-controls"></a>MFC – třídy pro cesty k datům v ovládacích prvcích ActiveX

Třídy MFC `CDataPathProperty` a [ccacheddatapathproperty –](../mfc/reference/ccacheddatapathproperty-class.md) implementovat vlastnosti ovládacího prvku ActiveX, které lze načíst asynchronně. Asynchronní vlastnosti jsou načteny po zahájení synchronní. Asynchronní ovládací prvky ActiveX opakovaně vyvolání zpětného volání k označení dostupnost nových dat systému exchange během dlouhých vlastnost.

`CDataPathProperty` je odvozen z `CAsyncMonikerFile`. `CCachedDataPathProperty` je odvozen z `CDataPathProperty`. K implementaci asynchronního vlastnosti v ovládacích prvků ActiveX, odvoďte třídu z `CDataPathProperty` nebo `CCachedDataPathProperty`a přepsat [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) a další oznámení, která chcete dostávat.

#### <a name="to-download-a-file-using-asynchronous-monikers"></a>Chcete-li stáhnout soubor přes asynchronní monikery

1. Deklarace třídy odvozené od [casyncmonikerfile –](../mfc/reference/casyncmonikerfile-class.md).

1. Přepsat [OnDataAvailable](../mfc/reference/casyncmonikerfile-class.md#ondataavailable) zobrazit data.

1. Přepsání dalších členských funkcí, včetně [OnProgress](../mfc/reference/casyncmonikerfile-class.md#onprogress), [OnStartBinding](../mfc/reference/casyncmonikerfile-class.md#onstartbinding), a [OnStopBinding](../mfc/reference/casyncmonikerfile-class.md#onstopbinding).

1. Deklarujte instanci této třídy a použít ho k otevírání adres URL.

Informace o stahování asynchronně v ovládacím prvku ActiveX naleznete v tématu [ovládací prvky Activexna Internetu](../mfc/activex-controls-on-the-internet.md).

## <a name="see-also"></a>Viz také

[Úlohy internetového programování MFC](../mfc/mfc-internet-programming-tasks.md)<br/>
[Základy internetového programování v prostředí MFC](../mfc/mfc-internet-programming-basics.md)

