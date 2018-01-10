---
title: "static_partitioner – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs: C++
helpviewer_keywords: static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2c7f41a2d2a592bff5e1f2217b39b6047d5093ad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="staticpartitioner-class"></a>static_partitioner – třída
`static_partitioner` Třída reprezentuje statické dělení vstupní přes podle rozsahu `parallel_for`. Dělicí metody rozdělí rozsahu na libovolný počet bloků dat jsou k dispozici pro Plánovač underyling pracovních procesů.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[static_partitioner](#ctor)|Vytvoří `static_partitioner` objektu.|  
|[~ static_partitioner – destruktor](#dtor)|Zničí `static_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `static_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a>~ static_partitioner 

 Zničí `static_partitioner` objektu.  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a>static_partitioner 

 Vytvoří `static_partitioner` objektu.  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
