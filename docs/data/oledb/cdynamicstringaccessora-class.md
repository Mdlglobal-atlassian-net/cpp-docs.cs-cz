---
title: "CDynamicStringAccessorA – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CDynamicStringAccessorA
dev_langs: C++
helpviewer_keywords: CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a9e7e2119bf25fda107ff529781efa5c517b01fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA – třída
Umožňuje přístup ke zdroji dat, pokud nemáte žádné znalosti schématu databáze (podkladová struktura).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## <a name="remarks"></a>Poznámky  
 Obě požadavku, že zprostředkovatel načíst všechna data z úložiště dat jako řetězce data, ale `CDynamicStringAccessor` požadavky ANSI řetězcová data.  
  
 `CDynamicStringAccessorA`dědí **GetString** a `SetString` z `CDynamicStringAccessor`. Při použití těchto metod v `CDynamicStringAccessorA` objekt, ***BaseType*** je **CHAR**.  
  
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