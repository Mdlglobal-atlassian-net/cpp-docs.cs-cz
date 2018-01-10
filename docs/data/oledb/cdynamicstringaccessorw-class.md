---
title: "CDynamicStringAccessorW – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDynamicStringAccessorW
dev_langs: C++
helpviewer_keywords: CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 90c97da001d6c8cfb10ddff2a61069adeccc8112
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obě požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data, ale `CDynamicStringAccessor` požadavky dat řetězců kódování Unicode.  
  
 `CDynamicStringAccessorW`dědí **GetString** a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorW` objekt, ***BaseType*** je **WCHAR**.  
  
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