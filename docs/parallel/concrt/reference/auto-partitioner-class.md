---
title: "auto_partitioner – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1cdb2cf5dcb149879be44c59714c5af6008c4b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="autopartitioner-class"></a>auto_partitioner – třída
`auto_partitioner` Třída reprezentuje výchozí metoda `parallel_for`, `parallel_for_each` a `parallel_transform` použít při vytváření oddílů se iteruje nad rozsahu. Tato metoda oddíly employes rozsahu krádež pro vyrovnávání zatížení a také za iteraci zrušení.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class auto_partitioner;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[auto_partitioner](#ctor)|Vytvoří `auto_partitioner` objektu.|  
|[~auto_partitioner Destructor](#dtor)|Zničí `auto_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `auto_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~auto_partitioner 

 Zničí `auto_partitioner` objektu.  
  
```
~auto_partitioner();
```  
  
##  <a name="ctor"></a> auto_partitioner 

 Vytvoří `auto_partitioner` objektu.  
  
```
auto_partitioner();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
