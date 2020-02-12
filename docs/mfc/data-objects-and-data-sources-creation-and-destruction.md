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
ms.openlocfilehash: c5bbc2b3e19278a397e13c9b936d2434570c581c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127415"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Datové objekty a zdroje dat: Vytváření a likvidace

Jak je vysvětleno v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md), datové objekty a zdroje dat reprezentují obě strany přenosu dat. Tento článek vysvětluje, kdy vytvořit a zničit tyto objekty a zdroje k tomu, aby se vaše datové přenosy správně prováděly, včetně těchto:

- [Vytváření datových objektů](#_core_creating_data_objects)

- [Zničení datových objektů](#_core_destroying_data_objects)

- [Vytváření zdrojů dat](#_core_creating_data_sources)

- [Zničení zdrojů dat](#_core_destroying_data_sources)

##  <a name="_core_creating_data_objects"></a>Vytváření datových objektů

Datové objekty jsou používány cílovou aplikací – buď klientem, nebo serverem. Datový objekt v cílové aplikaci je jedním z konců připojení mezi zdrojovou aplikací a cílovou aplikací. Datový objekt v cílové aplikaci se používá pro přístup k datům ve zdroji dat a k interakci s nimi.

Existují dvě běžné situace, kdy je datový objekt potřeba. První situací, kdy se data ve vaší aplikaci zahodí pomocí přetažení. Druhá situace je v případě, že je vybrána možnost vložit nebo Vložit jinak v nabídce Upravit.

V případě přetahování není nutné vytvářet datový objekt. Ukazatel na existující datový objekt bude předán vaší funkci `OnDrop`. Tento datový objekt je vytvořen rozhraním v rámci operace přetažení a bude také zničen. Nejedná se vždy o případ, kdy je vkládání provedeno jinou metodou. Další informace najdete v tématu [zničení datových objektů](#_core_destroying_data_objects).

Pokud aplikace provádí speciální operaci vložení nebo vložení, měli byste vytvořit objekt `COleDataObject` a zavolat jeho členskou funkci `AttachClipboard`. Tím se datový objekt přidružuje k datům ve schránce. Tento datový objekt pak můžete použít ve funkci vložení.

##  <a name="_core_destroying_data_objects"></a>Zničení datových objektů

Pokud budete postupovat podle schématu popsaného v [tématu Vytváření datových objektů](#_core_creating_data_objects), zničení datových objektů je triviálním aspektem datových přenosů. Datový objekt, který byl vytvořen v rámci funkce vložení, bude při návratu funkce vložení zničen knihovnou MFC.

Pokud budete postupovat podle jiné metody zpracování operací vložení, ujistěte se, že datový objekt je po dokončení operace vložení zničen. Dokud nebude datový objekt zničen, nebude možné v žádné aplikaci úspěšně kopírovat data do schránky.

##  <a name="_core_creating_data_sources"></a>Vytváření zdrojů dat

Zdroje dat se používají zdrojem přenosu dat, který může být buď klientem, nebo na straně serveru přenosu dat. Zdroj dat ve zdrojové aplikaci je jedním z konců připojení mezi zdrojovou aplikací a cílovou aplikací. Datový objekt v cílové aplikaci slouží k interakci s daty ve zdroji dat.

Zdroje dat se vytvoří, když aplikace potřebuje zkopírovat data do schránky. Typický scénář se spustí takto:

1. Uživatel vybere data.

1. Uživatel zvolí **kopírování** (nebo **vyjmutí**) z nabídky **Upravit** nebo spustí operaci přetažení.

1. V závislosti na návrhu programu vytvoří aplikace objekt `COleDataSource` nebo objekt ze třídy odvozené z `COleDataSource`.

1. Vybraná data jsou vložena do zdroje dat voláním jedné z funkcí ve skupinách `COleDataSource::CacheData` nebo `COleDataSource::DelayRenderData`.

1. Aplikace volá členskou funkci `SetClipboard` (nebo členskou funkci `DoDragDrop`, pokud se jedná o operaci přetažení) patřící k objektu vytvořenému v kroku 3.

1. Pokud se jedná o operaci **Vyjmout** nebo `DoDragDrop` vrátí **DROPEFFECT_MOVE**, data vybraná v kroku 1 se z dokumentu odstraní.

Tento scénář je implementován pomocí ukázek MFC OLE [OCLIENT](../overview/visual-cpp-samples.md) a [HIERSVR](../overview/visual-cpp-samples.md). Podívejte se na zdroj pro každou `CView`odvozenou třídu pro všechny kromě funkcí `GetClipboardData` a `OnGetClipboardData`. Tyto dvě funkce jsou buď v implementaci třídy odvozené od `COleClientItem` nebo `COleServerItem`. Tyto ukázkové programy poskytují dobrý příklad implementace těchto konceptů.

V případě, že chcete upravit výchozí chování operace přetažení, dojde k jiné situaci, kdy budete chtít vytvořit objekt `COleDataSource`. Další informace naleznete v tématu přetažení [OLE: přizpůsobení](../mfc/drag-and-drop-ole.md#customize-drag-and-drop) článku přetažení myší.

##  <a name="_core_destroying_data_sources"></a>Zničení zdrojů dat

Zdroje dat musí být zničeny aplikací, které jsou aktuálně zodpovědné za ně. V situacích, kdy jste zdrojem dat pro OLE, jako je například volání [COleDataSource –::D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop), je třeba volat `pDataSrc->InternalRelease`. Příklad:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Pokud jste zdroj dat nemuseli vyřadíte do OLE, zodpovídáte za jeho zničení, jako u všech typických C++ objektů.

Další informace najdete v tématu [přetahování](../mfc/drag-and-drop-ole.md), [Schránkování](../mfc/clipboard.md)a [manipulace s datovými objekty a zdroji dat](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Viz také

[Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject – třída](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource – třída](../mfc/reference/coledatasource-class.md)
