---
title: CDynamicStringAccessorA – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorA
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d6d05ac97846f55cf65d4010179b28d2b543ef66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33096480"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura).  
  
## <a name="syntax"></a>Syntaxe

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obě požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data, ale `CDynamicStringAccessor` požadavky ANSI řetězcová data.  
  
 `CDynamicStringAccessorA` dědí **GetString** a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorA` objekt, ***BaseType*** je **CHAR**.  
  
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