---
title: BEGIN_COLUMN_MAP | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- BEGIN_COLUMN_MAP
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_COLUMN_MAP macro
ms.assetid: d6ffe633-e0da-4e33-8faa-f7f259d05420
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 45d5438d1a4ba946aa3db36cc2b92eef1aa93ba3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="begincolumnmap"></a>BEGIN_COLUMN_MAP
Označuje začátek položku mapování sloupců.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
BEGIN_COLUMN_MAP(x)  
```  
  
#### <a name="parameters"></a>Parametry  
 *x*  
 [v] Název třídy záznamů uživatele odvozené z `CAccessor`.  
  
## <a name="remarks"></a>Poznámky  
 Toto makro se používá v případě jednoho přístupového objektu pro sadu řádků. Pokud máte několik přístupových objektů pro sadu řádků, použijte [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).  
  
 `BEGIN_COLUMN_MAP` Makro byla dokončena s `END_COLUMN_MAP` makro. Toto makro se používá při pouze jeden přistupujícího objektu potřebné v záznamu uživatele.  
  
 Sloupce odpovídají na pole v sadě řádků, které chcete vytvořit vazbu.  
  
## <a name="example"></a>Příklad  
 Zde je ukázka sloupce a parametr mapy:  
  
 <!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [END_COLUMN_MAP](../../data/oledb/end-column-map.md)   
 [COLUMN_ENTRY](../../data/oledb/column-entry.md)   
 [COLUMN_ENTRY_EX](../../data/oledb/column-entry-ex.md)