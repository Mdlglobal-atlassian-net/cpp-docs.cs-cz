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
ms.openlocfilehash: 182abe71ccc9552c113ebb114b4351178e48b096
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151861"
---
# <a name="clipboard-adding-other-formats"></a>Schránka: Přidání dalších formátů

Toto téma vysvětluje, jak rozšířit seznam podporovaných formátů, zejména pro podporu technologie OLE. Téma [schránky: Kopírování a vkládání dat](../mfc/clipboard-copying-and-pasting-data.md) popisuje minimální implementaci potřebných k podpoře zkopírováním a vložením ze schránky. Pokud je toto vše můžete implementovat, jsou pouze formáty umístili do schránky **CF_METAFILEPICT**, **CF_EMBEDSOURCE**, **CF_OBJECTDESCRIPTOR**a případně **CF_LINKSOURCE**. Většina aplikací bude potřebovat další formáty do schránky. než tyto tři.

##  <a name="_core_registering_custom_formats"></a> Registrace vlastních formátů

Pokud chcete vytvořit vlastní formáty, postupujte stejným způsobem můžete využít při registraci libovolné vlastní formát schránky: předat název formát, který se **RegisterClipboardFormat** fungovat a její návratová hodnota jako ID formátu.

##  <a name="_core_placing_formats_on_the_clipboard"></a> Formáty umístění do schránky

Chcete-li přidat další formáty těm, které jsou umístěny do schránky, je nutné přepsat `OnGetClipboardData` funkce ve třídě odvozené z buď `COleClientItem` nebo `COleServerItem` (v závislosti na tom, zda je nativní data, která mají být zkopírovány). V této funkci by měl použít následující postup.

#### <a name="to-place-formats-on-the-clipboard"></a>Formáty umístění do schránky

1. Vytvoření `COleDataSource` objektu.

1. Tento zdroj dat předat funkci, která přidá nativní datových formátů do seznamu podporovaných formátů voláním `COleDataSource::CacheGlobalData`.

1. Přidání standardní formáty voláním `COleDataSource::CacheGlobalData` pro každé standardní formát, které chcete podporovat.

Tento postup se používá v MFC OLE ukázkový program [HIERSVR](../overview/visual-cpp-samples.md) (Prozkoumat `OnGetClipboardData` členskou funkci **CServerItem** třídy). V této ukázce jediným rozdílem je, daný krok tři není implementovat, protože HIERSVR podporuje žádné standardní formáty.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Objekty a data zdroje dat OLE a jednotné přenosu dat](../mfc/data-objects-and-data-sources-ole.md)

- [OLE – přetažení](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Viz také:

[Schránka: Použití mechanismu schránky OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
