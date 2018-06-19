---
title: CDynamicAccessor::GetColumnType | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicAccessor.GetColumnType
- CDynamicAccessor::GetColumnType
- GetColumnType
- CDynamicAccessor.GetColumnType
- ATL::CDynamicAccessor::GetColumnType
dev_langs:
- C++
helpviewer_keywords:
- GetColumnType method
ms.assetid: ac96a2e9-6049-4eb5-9718-9f5f5446b74e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4e2b0ad31c96afd63424d07767f25327eabce3e8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33095167"
---
# <a name="cdynamicaccessorgetcolumntype"></a>CDynamicAccessor::GetColumnType
Načte datový typ zadaný sloupec.  
  
## <a name="syntax"></a>Syntaxe  
  
```
bool GetColumnType(DBORDINAL nColumn,   
  DBTYPE* pType) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `nColumn`  
 [v] Číslo sloupce. Sloupec čísel začínající číslem 1. Hodnota 0 odkazuje na sloupec záložku, pokud existuje.  
  
 `pType`  
 [out] Ukazatel na datový typ pro určený sloupec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí **true** v případě úspěchu nebo **false** při selhání.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [HODNOTA DBTYPE](https://msdn.microsoft.com/en-us/library/ms711251.aspx)