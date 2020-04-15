---
title: 'Schránka: Přidání dalších formátů'
ms.date: 11/04/2016
helpviewer_keywords:
- formats [MFC], Clipboard
- Clipboard, formats
- custom formats, placing on Clipboard
- custom formats
- registering custom Clipboard data formats
- custom Clipboard data formats
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
ms.openlocfilehash: 6f4e159cc1b6918843d4a164dcca88500eb7b038
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374610"
---
# <a name="clipboard-adding-other-formats"></a>Schránka: Přidání dalších formátů

Toto téma vysvětluje, jak rozbalit seznam podporovaných formátů, zejména pro podporu OLE. Téma [Schránka: Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md) popisuje minimální implementaci potřebnou k podpoře kopírování a vkládání ze schránky. Pokud je to vše, co implementujete, jsou pouze formáty umístěné ve schránce **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**a případně **CF_LINKSOURCE**. Většina aplikací bude potřebovat více formátů ve schránce než tyto tři.

## <a name="registering-custom-formats"></a><a name="_core_registering_custom_formats"></a>Registrace vlastních formátů

Chcete-li vytvořit vlastní formáty, postupujte stejným způsobem, který byste použili při registraci libovolného vlastního formátu schránky: předejte název formátu funkci **RegisterClipboardFormat** a použijte jeho vrácenou hodnotu jako ID formátu.

## <a name="placing-formats-on-the-clipboard"></a><a name="_core_placing_formats_on_the_clipboard"></a>Umístění formátů do schránky

Chcete-li přidat další formáty k těm, které `OnGetClipboardData` jsou umístěny ve schránce, musíte přepsat funkci ve třídě, kterou jste odvodili z jedné `COleClientItem` nebo `COleServerItem` (v závislosti na tom, zda jsou data, která mají být zkopírována, nativní). V této funkci byste měli použít následující postup.

#### <a name="to-place-formats-on-the-clipboard"></a>Umístění formátů do schránky

1. Vytvořte `COleDataSource` objekt.

1. Předejte tento zdroj dat funkci, která přidá nativní formáty dat `COleDataSource::CacheGlobalData`do seznamu podporovaných formátů voláním .

1. Přidejte standardní formáty voláním `COleDataSource::CacheGlobalData` pro každý standardní formát, který chcete podporovat.

Tato technika se používá ve vzorovém programu [HIERSVR](../overview/visual-cpp-samples.md) knihovny MFC OLE (zkontrolujte `OnGetClipboardData` členskou funkci třídy **CServerItem).** Jediný rozdíl v této ukázce je, že krok tři není implementován, protože HIERSVR nepodporuje žádné jiné standardní formáty.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Datové objekty OLE a zdroje dat a jednotný přenos dat](../mfc/data-objects-and-data-sources-ole.md)

- [OLE – přetažení](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Viz také

[Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
