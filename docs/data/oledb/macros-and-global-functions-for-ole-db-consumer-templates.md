---
title: "Makra a globální funkce pro šablony příjemců OLE DB | Microsoft Docs"
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
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 541425a073b4d179a20a33646844723d655f8160
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makra a globální funkce pro šablony příjemců OLE DB
Šablony příjemce technologie OLE DB patří následující makra a globální funkce:  
  
### <a name="global-functions"></a>Globální funkce  
  
|||  
|-|-|  
|[AtlTraceErrorRecords](../../data/oledb/atltraceerrorrecords.md)|Vypíše záznam chyby technologie OLE DB informace k výpisu zařízení, pokud se vrátí chyba.|  
  
### <a name="accessor-map-macros"></a>Makra Map přístupového objektu  
  
|||  
|-|-|  
|[BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)|Označuje začátek položku přistupujícího objektu.|  
|[BEGIN_ACCESSOR_MAP –](../../data/oledb/begin-accessor-map.md)|Označuje začátek položek mapování přistupujícího objektu.|  
|[END_ACCESSOR](../../data/oledb/end-accessor.md)|Označuje konec položku přistupujícího objektu.|  
|[END_ACCESSOR_MAP](../../data/oledb/end-accessor-map.md)|Označuje konec položek mapování přistupujícího objektu.|  
  
### <a name="column-map-macros"></a>Makra Map sloupce  
  
|||  
|-|-|  
|[BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)|Označuje začátek položek mapování sloupců ve třídě záznamu uživatele.|  
|[BLOB_ENTRY](../../data/oledb/blob-entry.md)|Použít k vytvoření vazby binární rozsáhlý objekt (binární rozsáhlý OBJEKT).|  
|[BLOB_ENTRY_LENGTH](../../data/oledb/blob-entry-length.md)|Sestavy délka sloupce dat objektů BLOB.|  
|[BLOB_ENTRY_LENGTH_STATUS](../../data/oledb/blob-entry-length-status.md)|Sestava je délka a stav sloupce dat objektů BLOB.|  
|[BLOB_ENTRY_STATUS](../../data/oledb/blob-entry-status.md)|Hlásí stav sloupce dat objektů BLOB.|  
|[BLOB_NAME](../../data/oledb/blob-name.md)|Použít k vytvoření vazby binární rozsáhlý objekt název sloupce.|  
|[BLOB_NAME_LENGTH](../../data/oledb/blob-name-length.md)|Sestavy délka sloupce dat objektů BLOB.|  
|[BLOB_NAME_LENGTH_STATUS](../../data/oledb/blob-name-length-status.md)|Sestava je délka a stav sloupce dat objektů BLOB.|  
|[BLOB_NAME_STATUS](../../data/oledb/blob-name-status.md)|Hlásí stav sloupce dat objektů BLOB.|  
|[BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md)|Představuje položku záložku na sadě řádků. Položky záložky je zvláštní druh položky sloupce.|  
|[COLUMN_ENTRY](../../data/oledb/column-entry.md)|Představuje vazbu ke konkrétní sloupec v databázi.|  
|[COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje `type`, *délka*, *přesnost*, `scale`, a *stav* parametry.|  
|[COLUMN_ENTRY_LENGTH](../../data/oledb/column-entry-length.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *délka* proměnné.|  
|[COLUMN_ENTRY_LENGTH_STATUS](../../data/oledb/column-entry-length-status.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *stav* a *délka* parametry.|  
|[COLUMN_ENTRY_PS](../../data/oledb/column-entry-ps.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *přesnost* a `scale` parametry.|  
|[COLUMN_ENTRY_PS_LENGTH](../../data/oledb/column-entry-ps-length.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *délka* proměnnou, *přesnost* a `scale` parametry.|  
|[COLUMN_ENTRY_PS_LENGTH_STATUS](../../data/oledb/column-entry-ps-length-status.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *stav* a *délka* proměnné, *přesnost* a `scale` parametry.|  
|[COLUMN_ENTRY_PS_STATUS](../../data/oledb/column-entry-ps-status.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *stav* proměnnou, *přesnost* a `scale` parametry.|  
|[COLUMN_ENTRY_STATUS](../../data/oledb/column-entry-status.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje *stav* proměnné.|  
|[COLUMN_ENTRY_TYPE](../../data/oledb/column-entry-type.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje `type` parametr.|  
|[COLUMN_ENTRY_TYPE_SIZE](../../data/oledb/column-entry-type-size.md)|Představuje vazbu ke konkrétní sloupec v databázi. Podporuje `type` a `size` parametry.|  
|[COLUMN_NAME](../../data/oledb/column-name.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu.|  
|[COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datový typ, velikost, přesnost, měřítko, délka sloupce a sloupec Stav.|  
|[COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délka sloupce.|  
|[COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci délka sloupce a stav.|  
|[COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnost a měřítko.|  
|[COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikace délky přesnost, měřítko a sloupce.|  
|[COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnost, měřítko, délka sloupce a sloupec Stav.|  
|[COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci přesnost, měřítko a sloupec Stav.|  
|[COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci sloupec Stav.|  
|[COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datového typu.|  
|[COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datový typ, přesnost a měřítko.|  
|[COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datový typ a velikost.|  
|[COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)|Představuje vazbu ke konkrétní sloupec v databázi podle názvu. Podporuje specifikaci datový typ a ve sloupci stav.|  
|[END_COLUMN_MAP](../../data/oledb/end-column-map.md)|Označuje konec položek mapování sloupců.|  
  
### <a name="command-macros"></a>Makra příkazů  
  
|||  
|-|-|  
|[DEFINE_COMMAND](../../data/oledb/define-command.md)|Určuje příkaz, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Je možné zadat pouze typy řetězec odpovídající typu zadané aplikace (ANSI nebo Unicode). Je doporučeno používat [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) místo `DEFINE_COMMAND`.|  
|[DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md)|Určuje příkaz, který se použije k vytvoření dané sadě řádků při použití [CCommand](../../data/oledb/ccommand-class.md) třídy. Podporuje aplikace, ANSI a Unicode.|  
  
### <a name="parameter-map-macros"></a>Makra Map parametr  
  
|||  
|-|-|  
|[BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md)|Označuje začátek položek mapování parametru ve třídě záznamu uživatele.|  
|[END_PARAM_MAP](../../data/oledb/end-param-map.md)|Označuje konec položek mapování parametru.|  
|[SET_PARAM_TYPE](../../data/oledb/set-param-type.md)|Určuje `COLUMN_ENTRY` makra, které následují `SET_PARAM_TYPE` makro jako vstupní, výstupní nebo vstupu a výstupu.|  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)