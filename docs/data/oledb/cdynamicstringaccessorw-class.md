---
title: CDynamicStringAccessorW – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorW
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 767add2be1f9f5266a6a66ce4455dec172f63e45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura).  
  
## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obě požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data, ale `CDynamicStringAccessor` požadavky dat řetězců kódování Unicode.  
  
 `CDynamicStringAccessorW` dědí **GetString** a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorW` objekt, ***BaseType*** je **WCHAR**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: také atldbcli.h  
  
## <a name="see-also"></a>Viz také  
 [Šablony příjemce technologie OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referenční dokumentace šablony příjemců OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor – třída](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor – třída](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor – třída](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor – třída](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor – třída](../../data/oledb/cdynamicstringaccessor-class.md)