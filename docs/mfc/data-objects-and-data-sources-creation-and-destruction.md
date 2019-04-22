---
title: 'Datové objekty a zdroje dat: Vytváření a likvidace'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: 68ee5fbfec554df8865ca50c265ca2fa2f226a29
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58775241"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Datové objekty a zdroje dat: Vytváření a likvidace

Jak je popsáno v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md), datové objekty a zdroje dat představují obou stranách přenosu dat. Tento článek vysvětluje, kdy se má vytvořit a zničit tyto objekty a zdroje provádět datové přenosy správně, včetně:

- [Vytváření datových objektů](#_core_creating_data_objects)

- [Zničení datových objektů](#_core_destroying_data_objects)

- [Vytváření zdroje dat](#_core_creating_data_sources)

- [Zničení zdroje dat](#_core_destroying_data_sources)

##  <a name="_core_creating_data_objects"></a> Vytváření datových objektů

Datové objekty se používají podle cílové aplikace, klienta nebo serveru. Datový objekt v cílové aplikaci je jeden konec připojení mezi aplikací zdrojové a cílové aplikace. Datový objekt v cílové aplikaci se používají pro přístup k interakci s daty v datovém zdroji.

Existují dva běžné situace, kdy je potřeba datový objekt. První situace je při přetažení dat ve vaší aplikaci pomocí přetažení. Druhá situace je při překopírování nebo vložení speciální výběru z nabídky upravit.

V případě přetahování myší není potřeba vytvoření datového objektu. Ukazatel na existující objekt data se předají do vaší `OnDrop` funkce. Tento datový objekt se vytvoří v rámci rozhraní jako součást operace přetažení myší a také zničí jím. To není vždy případu při vkládání provádí jinou metodu. Další informace najdete v tématu [zničení datových objektů](#_core_destroying_data_objects).

Pokud aplikace provádí vkládání nebo speciální operace vložení, měli byste vytvořit `COleDataObject` objektu a volání jeho `AttachClipboard` členskou funkci. Tento datový objekt přidruží data do schránky. Potom můžete tento datový objekt ve své funkci Vložit.

##  <a name="_core_destroying_data_objects"></a> Zničení datových objektů

Pokud budete postupovat podle schématu je popsáno v [vytváření datových objektů](#_core_creating_data_objects), zničení datových objektů je triviální aspekt datové přenosy. Datový objekt, který byl vytvořen ve své funkci Vložit zničí v prostředí MFC návratu Vložit funkci.

Pokud budete postupovat podle jiný způsob zpracování operací vložení, zkontrolujte, zda že datový objekt je zničen po dokončení operace vložení. Dokud datový objekt je zničen, nebude možné pro každou aplikaci úspěšně zkopírovat data do schránky.

##  <a name="_core_creating_data_sources"></a> Vytváření zdroje dat

Zdroje dat jsou používány zdroji přenosu dat, který může být klient nebo přenosu dat na straně serveru. Zdroj dat ve zdrojové aplikaci je jeden konec připojení mezi aplikací zdrojové a cílové aplikace. Datový objekt v cílové aplikaci slouží k interakci s daty v datovém zdroji.

Zdroje dat se vytvoří, když aplikace potřebuje ke kopírování dat do schránky. Typický scénář spustí takto:

1. Uživatel vybere nějaká data.

1. Uživatel vybere **kopírování** (nebo **Vyjmout**) z **upravit** nabídky nebo začne operace přetažení myší.

1. V závislosti na návrhu aplikace, aplikace vytvoří buď `COleDataSource` objekt nebo objekt ze třídy odvozené z `COleDataSource`.

1. Vybraná data je vložen do zdroje dat voláním jedné z funkcí v `COleDataSource::CacheData` nebo `COleDataSource::DelayRenderData` skupiny.

1. Volání aplikace `SetClipboard` členskou funkci (nebo `DoDragDrop` členskou funkci, pokud se jedná o operaci přetažení myší) patřící do objekt vytvořený v kroku 3.

1. Pokud se jedná **Vyjmout** operace nebo `DoDragDrop` vrátí **DROPEFFECT_MOVE**, vybrali v kroku 1, data se odstraní z dokumentu.

Tento scénář je implementováno ukázky MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md). Podívejte se na zdroje pro každou aplikaci `CView`-odvozené třídy pro všechny kromě na `GetClipboardData` a `OnGetClipboardData` funkce. Tyto dvě funkce jsou buď `COleClientItem` nebo `COleServerItem`– implementace třídy odvozené. Tyto ukázkové programy poskytují dobrý příklad toho, jak implementovat tyto koncepty.

Jeden další situace, ve kterém můžete chtít vytvořit `COleDataSource` objekt nastane, pokud chcete upravit výchozí chování operace přetažení myší. Další informace najdete v tématu [přetažení: Přizpůsobení](../mfc/drag-and-drop-customizing.md) článku.

##  <a name="_core_destroying_data_sources"></a> Zničení zdroje dat

Zdroje dat musí být zničený aktuálně za jejich aplikací. V situacích, kde předáte zdroje dat OLE, jako například volání [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), je třeba volat `pDataSrc->InternalRelease`. Příklad:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Pokud zdroj dat dosud předán OLE, pak budete muset pro zničení, stejně jako u jakékoli typické objekt jazyka C++.

Další informace najdete v tématu [přetažení](../mfc/drag-and-drop-ole.md), [schránky](../mfc/clipboard.md), a [manipulace s datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Viz také:

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
