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
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371214"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Datové objekty a zdroje dat: Vytváření a likvidace

Jak je vysvětleno v článku [Datové objekty a zdroje dat (OLE),](../mfc/data-objects-and-data-sources-ole.md)datové objekty a zdroje dat představují obě strany přenosu dat. Tento článek vysvětluje, kdy vytvořit a zničit tyto objekty a zdroje pro správné provádění přenosů dat, včetně:

- [Vytváření datových objektů](#_core_creating_data_objects)

- [Zničení datových objektů](#_core_destroying_data_objects)

- [Vytváření zdrojů dat](#_core_creating_data_sources)

- [Zničení zdrojů dat](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Vytváření datových objektů

Datové objekty jsou používány cílovou aplikací – klientem nebo serverem. Datový objekt v cílové aplikaci je jedním z konce spojení mezi zdrojovou aplikací a cílovou aplikací. Datový objekt v cílové aplikaci se používá pro přístup k datům ve zdroji dat a interakci s nimi.

Existují dvě běžné situace, kdy je potřeba datový objekt. První situace je, když data jsou vynechány v aplikaci pomocí přetažení. Druhá situace je, když vložit nebo vložit jinak je vybrán z nabídky Upravit.

V případě přetažení není nutné vytvářet datový objekt. Ukazatel na existující datový objekt bude `OnDrop` předán vaší funkci. Tento datový objekt je vytvořen rámci jako součást operace přetažení a bude také zničen. To není vždy případ při vkládání se provádí jinou metodou. Další informace naleznete v [tématu Zničení datových objektů](#_core_destroying_data_objects).

Pokud aplikace provádí operaci vložení nebo vložení speciální, `COleDataObject` měli byste `AttachClipboard` vytvořit objekt a volat jeho člennou funkci. Tím přidružíte datový objekt k datům ve schránce. Tento datový objekt pak můžete použít ve funkci vložení.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Zničení datových objektů

Pokud budete postupovat podle schématu popsaného v [části Vytváření datových objektů](#_core_creating_data_objects), zničení datových objektů je triviální aspekt přenosů dat. Datový objekt, který byl vytvořen ve funkci vložení, bude zničen knihovnou MFC, když se vrátí funkce vložení.

Pokud budete postupovat podle jiné metody zpracování operací vložení, ujistěte se, že datový objekt je zničen po dokončení operace vložení. Dokud nebude datový objekt zničen, nebude možné, aby jakákoli aplikace úspěšně zkopírovala data do schránky.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Vytváření zdrojů dat

Zdroje dat jsou používány zdrojem přenosu dat, což může být klientská nebo serverová strana přenosu dat. Zdroj dat ve zdrojové aplikaci je jedním z konce spojení mezi zdrojovou aplikací a cílovou aplikací. Datový objekt v cílové aplikaci se používá k interakci s daty ve zdroji dat.

Zdroje dat jsou vytvořeny, když aplikace potřebuje zkopírovat data do schránky. Typický scénář běží takto:

1. Uživatel vybere některá data.

1. Uživatel zvolí **kopírovat** (nebo **vyjmout)** z nabídky **Úpravy** nebo zahájí operaci přetažení myší.

1. V závislosti na návrhu programu aplikace `COleDataSource` vytvoří objekt nebo objekt z `COleDataSource`třídy odvozené z aplikace .

1. Vybraná data se vloží do zdroje dat voláním `COleDataSource::CacheData` jedné `COleDataSource::DelayRenderData` z funkcí ve skupinách nebo.

1. Aplikace volá `SetClipboard` členská funkce `DoDragDrop` (nebo členská funkce, pokud se jedná o operaci přetažení) patřící k objektu vytvořenému v kroku 3.

1. Pokud se jedná o `DoDragDrop` operaci **Vyjmout** nebo vrátí **DROPEFFECT_MOVE**, data vybraná v kroku 1 se odstraní z dokumentu.

Tento scénář je implementována vzorky Knihovny MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md). Podívejte se na zdroj pro `CView`každou aplikaci odvozené `GetClipboardData` `OnGetClipboardData` třídy pro všechny, ale a funkce. Tyto dvě funkce jsou `COleClientItem` `COleServerItem`v implementaci třídy nebo odvozené. Tyto ukázkové programy poskytují dobrý příklad, jak implementovat tyto koncepty.

Jedna další situace, ve které `COleDataSource` můžete chtít vytvořit objekt dochází, pokud upravujete výchozí chování operace přetaženímyší. Další informace naleznete v [článku Ole Drag and drop: Customize drag and drop](../mfc/drag-and-drop-ole.md#customize-drag-and-drop) article .

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Zničení zdrojů dat

Zdroje dat musí být zničeny aplikací, která je za ně v současné době odpovědná. V situacích, kdy předáte zdroj dat ole, například volání [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), je třeba volat `pDataSrc->InternalRelease`. Příklad:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Pokud jste nepředali zdroj dat OLE, pak jste zodpovědní za jeho zničení, stejně jako u všech typických objektů Jazyka C++.

Další informace naleznete v tématech [Přetažení](../mfc/drag-and-drop-ole.md), [Schránka](../mfc/clipboard.md)a [Manipulace s datovými objekty a zdroji dat](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Viz také

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[Třída COleDataSource](../mfc/reference/coledatasource-class.md)
