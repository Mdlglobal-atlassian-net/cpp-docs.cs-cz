---
title: "Makra pro šablony zprostředkovatele technologie OLE DB | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.templates.ole
dev_langs: C++
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 11a5ae3d0ba5c3da517a380adf795e579d0dce51
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="macros-for-ole-db-provider-templates"></a>Makra pro šablony zprostředkovatele OLE DB
Makra zprostředkovatele šablony technologie OLE DB nabízejí funkce v následujících kategorií:  
  
### <a name="property-set-map-macros"></a>Makra mapy sady vlastností  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](../../data/oledb/begin-property-set.md)|Označuje začátek sadu vlastností.|  
|[BEGIN_PROPERTY_SET_EX](../../data/oledb/begin-property-set-ex.md)|Označuje začátek sadu vlastností.|  
|[BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md)|Značky začátku vlastnost nastavena, které můžete skrytý nebo definované mimo obor zprostředkovatele.|  
|[CHAIN_PROPERTY_SET](../../data/oledb/chain-property-set.md)|Vlastnost skupiny řetězy společně.|  
|[END_PROPERTY_SET](../../data/oledb/end-property-set.md)|Označuje konec sadu vlastností.|  
|[END_PROPSET_MAP](../../data/oledb/end-propset-map.md)|Označuje konec mapy sady vlastností.|  
|[PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)|Nastaví konkrétní vlastnost v vlastností nastavenou na výchozí hodnotu.|  
|[PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md)|Nastaví určitou vlastnost pro vlastnost nastavená na hodnotu poskytl vám. Můžete také nastavit příznaky a možnosti.|  
|[PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md)|Nastaví určitou vlastnost pro vlastnost nastavená na hodnotu poskytl vám.|  
  
### <a name="column-map-macros"></a>Makra Map sloupce  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md)|Označuje začátek položky mapy sloupce zprostředkovatele.|  
|[END_PROVIDER_COLUMN_MAP](../../data/oledb/end-provider-column-map.md)|Označuje konec položky mapy sloupce zprostředkovatele.|  
|[PROVIDER_COLUMN_ENTRY](../../data/oledb/provider-column-entry.md)|Představuje konkrétní sloupec podporována zprostředkovatelem.|  
|[PROVIDER_COLUMN_ENTRY_GN](../../data/oledb/provider-column-entry-gn.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Zadávat lze velikosti sloupce, datový typ, přesnost, měřítko a identifikátor GUID sady řádků schématu.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](../../data/oledb/provider-column-entry-fixed.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Zadaný datový typ sloupce.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Můžete zadat velikost sloupce.|  
|[PROVIDER_COLUMN_ENTRY_STR](../../data/oledb/provider-column-entry-str.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Předpokládá se, že typ sloupce je řetězec.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](../../data/oledb/provider-column-entry-type-length.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Jako PROVIDER_COLUMN_ENTRY_LENGTH, ale také vám umožní určit typ sloupce dat, jakož i velikost.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](../../data/oledb/provider-column-entry-wstr.md)|Představuje konkrétní sloupec podporována zprostředkovatelem. Předpokládá se, že typ sloupce je řetězec znaků Unicode.|  
  
### <a name="schema-rowset-macros"></a>Makra sada řádků schématu  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](../../data/oledb/begin-schema-map.md)|Označuje začátek mapu schématu.|  
|[SCHEMA_ENTRY](../../data/oledb/schema-entry.md)|Přiřadí identifikátor GUID s třídou.|  
|[END_SCHEMA_MAP](../../data/oledb/end-schema-map.md)|Označuje konec mapu schématu.|  
  
## <a name="see-also"></a>Viz také  
 [Šablony zprostředkovatele technologie OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Architektura šablon zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Referenční dokumentace šablony zprostředkovatele OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)