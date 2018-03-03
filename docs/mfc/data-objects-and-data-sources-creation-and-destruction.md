---
title: "Datové objekty a zdroje dat: vytváření a likvidace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28d468bef2eee05600b4d298f966533a7e6bc025
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Datové objekty a zdroje dat: Vytváření a likvidace
Jak je popsáno v článku [datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md), datové objekty a zdroje dat představuje obou stranách datových přenosů. Tento článek vysvětluje, kdy se má vytvořit a odstraňte tyto objekty a zdroje k provedení vaší přenosů dat správně, včetně:  
  
-   [Vytváření datových objektů](#_core_creating_data_objects)  
  
-   [Zničení datových objektů](#_core_destroying_data_objects)  
  
-   [Vytváření zdroje dat](#_core_creating_data_sources)  
  
-   [Zničení zdroje dat](#_core_destroying_data_sources)  
  
##  <a name="_core_creating_data_objects"></a>Vytváření datových objektů  
 Datové objekty jsou používány cílové aplikaci – Klient nebo server. Objekt dat do cílové aplikace je jeden element end připojení mezi aplikací zdrojové a cílové aplikaci. Objekt dat do cílové aplikace se používá pro přístup k a interagovat s daty v datovém zdroji.  
  
 Existují dvě běžné situace, kdy je potřeba na datový objekt. První situace je při přetažení data do vaší aplikace pomocí operace přetažení. V druhém případě je při vkládání nebo Vložit jinak výběru z nabídky Úpravy.  
  
 V případě, že přetahování myší není potřeba vytvořit datový objekt. Ukazatele na existující objekt dat se předá vaší `OnDrop` funkce. Tento datový objekt se vytvoří rámcem v rámci operace přetahování myší a bude také zničí ho. To není vždy případě při vkládání se provádí jinou metodu. Další informace najdete v tématu [zničení datových objektů](#_core_destroying_data_objects).  
  
 Pokud aplikace provádí vložení nebo speciální operaci vložení, měli byste vytvořit `COleDataObject` objekt a volání jeho `AttachClipboard` – členská funkce. Tento datový objekt přidruží data do schránky. Pak může použít tento datový objekt vložit funkci.  
  
##  <a name="_core_destroying_data_objects"></a>Zničení datových objektů  
 Pokud budete postupovat podle schématu popsané v [vytváření datových objektů](#_core_creating_data_objects), zničení datových objektů je trivial aspekt datových přenosů. Datový objekt, který byl vytvořen v Vložit funkci bude zničí MFC po návratu Vložit funkci.  
  
 Pokud budete postupovat podle jiný způsob zpracování operace vkládání, zkontrolujte, zda že datový objekt je zrušen po dokončení operaci vložení. Dokud datový objekt zničení, nebude možné pro všechny aplikace úspěšně zkopírovat data do schránky.  
  
##  <a name="_core_creating_data_sources"></a>Vytváření zdroje dat  
 Zdroje dat jsou používány zdroj přenos dat, což může být klientovi nebo přenos dat na straně serveru. Zdroj dat v aplikaci zdroj je jeden element end připojení mezi aplikací zdrojové a cílové aplikaci. Objekt dat do cílové aplikace se používá k interakci s daty v datovém zdroji.  
  
 Zdroje dat se vytvoří, když aplikace potřebuje ke kopírování dat do schránky. Typický scénář spustí takto:  
  
1.  Uživatel vybere některá data.  
  
2.  Uživatel vybere **kopie** (nebo **Vyjmout**) z **upravit** nabídky nebo zahájí operaci přetažení myší.  
  
3.  V závislosti na návrh programu, vytvoří aplikace buď `COleDataSource` objekt nebo objekt ze třídy odvozené od `COleDataSource`.  
  
4.  Vybrané, vloží se data do zdroje dat voláním jedna z funkcí v `COleDataSource::CacheData` nebo `COleDataSource::DelayRenderData` skupiny.  
  
5.  Volání aplikace `SetClipboard` – členská funkce (nebo `DoDragDrop` – členská funkce, pokud se jedná o operaci přetažení myší) patřící do objekt vytvořený v kroku 3.  
  
6.  Pokud je to **Vyjmout** operaci nebo `DoDragDrop` vrátí `DROPEFFECT_MOVE`, data vybrali v kroku 1 se odstraní z dokumentu.  
  
 Tento scénář je implementováno modulem ukázky MFC OLE [OCLIENT](../visual-cpp-samples.md) a [HIERSVR](../visual-cpp-samples.md). Podívejte se na zdroj pro každou aplikaci `CView`-odvozené třídy pro všechny ale na `GetClipboardData` a `OnGetClipboardData` funkce. Tyto dvě funkce jsou buď `COleClientItem` nebo `COleServerItem`– implementace třídy odvozené. Tyto programy ukázka zadejte dobrým příkladem toho, jak implementovat tyto koncepty.  
  
 Jeden další situace, ve kterém můžete chtít vytvořit `COleDataSource` objekt vyskytuje, chcete-li změnit výchozí chování operací přetažení myší. Další informace najdete v tématu [přetažení: přizpůsobení](../mfc/drag-and-drop-customizing.md) článku.  
  
##  <a name="_core_destroying_data_sources"></a>Zničení zdroje dat  
 Zdroje dat musí být zničený aktuálně zodpovědná za je aplikací. V situacích, kde ruční zdroje dat OLE, jako například volání [COleDataSource::DoDragDrop](../mfc/reference/coledatasource-class.md#dodragdrop), je třeba volat **pDataSrc -> internalrelease –**. Příklad:  
  
 [!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]  
  
 Pokud jste ještě předávány zdroje dat OLE, pak jste zodpovědní za zničení, stejně jako u všech typické C++ objektů.  
  
 Další informace najdete v tématu [přetažení](../mfc/drag-and-drop-ole.md), [schránky](../mfc/clipboard.md), a [manipulace s datové objekty a zdroje dat](../mfc/data-objects-and-data-sources-manipulation.md).  
  
## <a name="see-also"></a>Viz také  
 [Datové objekty a zdroje dat (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject – třída](../mfc/reference/coledataobject-class.md)   
 [COleDataSource – třída](../mfc/reference/coledatasource-class.md)
