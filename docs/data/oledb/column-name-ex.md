---
title: COLUMN_NAME_EX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- COLUMN_NAME_EX
dev_langs:
- C++
helpviewer_keywords:
- COLUMN_NAME_EX macro
ms.assetid: 4f916a85-f6ae-464a-9cbe-0a56dbb274a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3992a727519ed83a0dbf4c570bad3bbf8d0404ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="columnnameex"></a>COLUMN_NAME_EX
Představuje vazbu na sadě řádků konkrétní sloupec v dané sadě řádků. Podobně jako [COLUMN_NAME](../../data/oledb/column-name.md)kromě toho, že tento makro také trvá datový typ, velikost, přesnost, měřítko, délka sloupce a sloupec Stav.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszName`  
 [v] Ukazatel na název sloupce. Název musí být řetězec znaků Unicode. Toho lze dosáhnout vložením "L" před název, například: `L"MyColumn"`.  
  
 `wType`  
 [v] Datový typ  
  
 `nLength`  
 [v] Velikost dat v bajtech.  
  
 `nPrecision`  
 [v] Maximální přesnost pro použití při získávání dat a `wType` je `DBTYPE_NUMERIC`. Tento parametr, jinak hodnota se ignoruje.  
  
 `nScale`  
 [v] Měřítko pro použití při získávání dat a `wType` je `DBTYPE_NUMERIC` nebo **DBTYPE_DECIMAL**.  
  
 `data`  
 [v] Odpovídající datových členů v záznamu uživatele.  
  
 *Délka*  
 [v] Proměnná vázat délka sloupce.  
  
 *Stav*  
 [v] Proměnná bylo vázané na sloupec Stav.  
  
## <a name="remarks"></a>Poznámky  
 V tématu [COLUMN_NAME](../../data/oledb/column-name.md) informace o umístění **COLUMN_NAME_\***  se používají makra.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Makra a globální funkce pro šablony příjemců OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)   
 [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md)   
 [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)   
 [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md)   
 [COLUMN_NAME](../../data/oledb/column-name.md)   
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
 [COLUMN_NAME_TYPE_STATUS](../../data/oledb/column-name-type-status.md)