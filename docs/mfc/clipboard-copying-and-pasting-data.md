---
title: 'Schránka: Kopírování a vkládání dat'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: cff9094315dc97e2040eb4dbad25d044c7c51a81
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58776099"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schránka: Kopírování a vkládání dat

Toto téma popisuje minimální práce, které jsou nezbytné k implementaci zkopírováním a vložením ze schránky ve vašich aplikacích OLE. Doporučujeme, abyste si přečetli [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md) témata než budete pokračovat.

Než budete moct implementovat kopírování nebo vkládání, je nutné zadat funkce pro zpracování možnosti kopírování, vyjmutí a vložení v nabídce Úpravy.

##  <a name="_core_copying_or_cutting_data"></a> Kopírování nebo vyjmutí dat

#### <a name="to-copy-data-to-the-clipboard"></a>Ke zkopírování dat do schránky.

1. Určení, zda data, která mají být zkopírovány je nativní dat nebo je to položka, vložený nebo připojený.

   - Pokud data vložené nebo propojené, získání ukazatele na `COleClientItem` objekt, který byl vybrán.

   - Pokud je nativní data a aplikace je server, vytvořit nový objekt odvozený od `COleServerItem` obsahující vybraná data. V opačném případě vytvořte `COleDataSource` objekt pro data.

1. Volání vybranou položku `CopyToClipboard` členskou funkci.

1. Pokud uživatel vybral vyjmutí operace místo operace kopírování, odstranění vybraných dat z vaší aplikace.

Příklad této sekvence najdete v tématu `OnEditCut` a `OnEditCopy` funkce v MFC OLE ukázkové programy [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md). Všimněte si, že tyto ukázky údržbu ukazatel aktuálně vybraného data, aby bylo kroku 1 je již dokončena.

##  <a name="_core_pasting_data"></a> Vkládání dat

Vkládání dat je složitější než zkopírováním, protože je nutné zvolit formát používané k vložení dat do vaší aplikace.

#### <a name="to-paste-data-from-the-clipboard"></a>K vložení dat ze schránky

1. V zobrazení třídy implementovat `OnEditPaste` zpracování uživatelů vyberete možnost Vložit v nabídce Úpravy.

1. V `OnEditPaste` funkce, vytváření `COleDataObject` objektu a volání jeho `AttachClipboard` členskou funkci pro tento objekt propojit data do schránky.

1. Volání `COleDataObject::IsDataAvailable` ke kontrole, jestli konkrétní formát je k dispozici.

   Alternativně můžete použít `COleDataObject::BeginEnumFormats` vás pod rouškou pro ostatní formáty najděte nejvíce vhodné pro vaši aplikaci.

1. Operace vložení formátu.

Příklad toho, jak to funguje, najdete v části implementace `OnEditPaste` členské funkce v zobrazení tříd definovaných v aplikacích MFC OLE ukázka [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
>  Hlavní výhodou oddělení operaci vložení do samostatné funkce je, že stejný kód pro vložení je možné při přetažení dat ve vaší aplikaci během operace přetažení myší. Stejně jako v OCLIENT a HIERSVR vaše `OnDrop` funkce může volat také `DoPasteItem`, opětovné použití kódu napsaného pro implementaci operace vložení.

Pro zpracování možnost Vložit jinak v nabídce Upravit, naleznete v tématu [dialogová okna v prostředí OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)

- [Objekty a data zdroje dat OLE a jednotné přenosu dat](../mfc/data-objects-and-data-sources-ole.md)

- [OLE – přetažení](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Viz také:

[Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
