---
title: COLUMN_NAME_TYPE_STATUS | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COLUMN_NAME_TYPE_STATUS
dev_langs: C++
helpviewer_keywords: COLUMN_NAME_TYPE_STATUS macro
ms.assetid: 72ad3728-5b3e-4131-9f38-835d776529d9
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 63bd0e84b9979e29219c678378822fade6487c72
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="columnnametypestatus"></a>COLUMN_NAME_TYPE_STATUS
Představuje vazbu na sadě řádků konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md)kromě toho, že tento makro také trvá datový typ a ve sloupci stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
COLUMN_NAME_TYPE_STATUS(  
pszName  
,   
wType  
,   
status  
,   
data  
 )  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [v] Ukazatel na název sloupce. Název musí být řetězec znaků Unicode. Toho lze dosáhnout vložením "L" před název, například: `L"MyColumn"`.  
  
 `wType`  
 [v] Datový typ  
  
 *Stav*  
 [v] Proměnná bylo vázané na sloupec Stav.  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [COLUMN_NAME](../../data/oledb/column-name.md) informace o umístění **COLUMN_NAME_\***  se používají makra.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP –](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
 [COLUMN_NAME_EX](../../data/oledb/column-name-ex.md)   
 [COLUMN_NAME_LENGTH](../../data/oledb/column-name-length.md)   
 [COLUMN_NAME_LENGTH_STATUS](../../data/oledb/column-name-length-status.md)   
 [COLUMN_NAME_STATUS](../../data/oledb/column-name-status.md)   
 [COLUMN_NAME_PS](../../data/oledb/column-name-ps.md)   
 [COLUMN_NAME_PS_LENGTH](../../data/oledb/column-name-ps-length.md)   
 [COLUMN_NAME_PS_STATUS](../../data/oledb/column-name-ps-status.md)   
 [COLUMN_NAME_PS_LENGTH_STATUS](../../data/oledb/column-name-ps-length-status.md)   
 [COLUMN_NAME_TYPE](../../data/oledb/column-name-type.md)   
 [COLUMN_NAME_TYPE_PS](../../data/oledb/column-name-type-ps.md)   
 [COLUMN_NAME_TYPE_SIZE](../../data/oledb/column-name-type-size.md)