---
title: 'Schránka: Kopírování a vkládání dat'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374569"
---
# <a name="clipboard-copying-and-pasting-data"></a>Schránka: Kopírování a vkládání dat

Toto téma popisuje minimální práci potřebnou k implementaci kopírování a vkládání ze schránky v aplikaci OLE. Před pokračováním doporučujeme přečíst témata [o objektech dat a zdrojích dat (OLE).](../mfc/data-objects-and-data-sources-ole.md)

Před implementací kopírování nebo vkládání musíte nejprve zadat funkce pro zpracování voleb Kopírovat, Vyjmout a Vložit v nabídce Úpravy.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Kopírování nebo řezání dat

#### <a name="to-copy-data-to-the-clipboard"></a>Kopírování dat do schránky

1. Určete, zda jsou data, která mají být zkopírována, nativní mise nebo zda se jedná o vložená nebo propojená položka.

   - Pokud jsou data vložena nebo propojena, `COleClientItem` získejte ukazatel na vybraný objekt.

   - Pokud jsou data nativní a aplikace je server, vytvořte nový objekt odvozený z `COleServerItem` obsahující vybraná data. V opačném `COleDataSource` případě vytvořte objekt pro data.

1. Volání `CopyToClipboard` členské funkce vybrané položky.

1. Pokud uživatel zvolil operaci vyjmutí namísto operace kopírování, odstraňte vybraná data z aplikace.

Příklad této sekvence naleznete `OnEditCut` v části `OnEditCopy` funkce a ve vzorových programech [MFC](../overview/visual-cpp-samples.md) OLE OCLIENT a [HIERSVR](../overview/visual-cpp-samples.md). Všimněte si, že tyto ukázky udržovat ukazatel na aktuálně vybraná data, takže krok 1 je již dokončena.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Vkládání dat

Vkládání dat je složitější než kopírování, protože je třeba zvolit formát, který chcete použít při vkládání dat do aplikace.

#### <a name="to-paste-data-from-the-clipboard"></a>Vložení dat ze schránky

1. Ve třídě zobrazení `OnEditPaste` implementujte, abyste zrekonstitovali, aby uživatelé zvolili možnost Vložit z nabídky Úpravy.

1. Ve `OnEditPaste` funkci vytvořte `COleDataObject` objekt a `AttachClipboard` zavolejte jeho členskou funkci, abyste tento objekt propojili s daty ve schránce.

1. Volání `COleDataObject::IsDataAvailable` zkontrolovat, zda je k dispozici určitý formát.

   Alternativně můžete vyhledat `COleDataObject::BeginEnumFormats` jiné formáty, dokud nenajdete jeden nejvhodnější pro vaši aplikaci.

1. Proveďte vložení formátu.

Příklad toho, jak to funguje, naleznete `OnEditPaste` v implementaci členských funkcí v třídách zobrazení definovaných ve vzorových programech MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md).

> [!TIP]
> Hlavní výhodou oddělení operace vložení do vlastní funkce je, že stejný kód vložení lze použít při vynechání dat v aplikaci během operace přetažení myší. Stejně jako v OCLIENT `OnDrop` a HIERSVR, vaše funkce může také volat `DoPasteItem`, opětovné použití kódu napsaného k implementaci operace vložení.

Chcete-li zpracovat volbu Vložit jinak v nabídce Úpravy, přečtěte si téma [Dialogová okna v OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Přidání dalších formátů](../mfc/clipboard-adding-other-formats.md)

- [Datové objekty OLE a zdroje dat a jednotný přenos dat](../mfc/data-objects-and-data-sources-ole.md)

- [OLE – přetažení](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Viz také

[Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
