---
title: "affinity_partitioner – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ecc7e20947eee2491bf806f225178724b268ace
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner – třída
`affinity_partitioner` Třídy je podobná `static_partitioner` třídy, ale zvyšuje mezipaměti spřažení podle svého výběru mapování podrozsahů na pracovních vláken. Ho může výrazně zvýšit výkon při smyčku je znovu spustit přes stejnou sadu dat a zda je data v mezipaměti. Všimněte si, že stejný `affinity_partitioner` objekt musí být použit s následující iterace paralelní smyčky, která je spuštěna v rámci konkrétní sady dat, abyste mohli využívat výhod polohu data.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[affinity_partitioner](#ctor)|Vytvoří `affinity_partitioner` objektu.|  
|[~affinity_partitioner Destructor](#dtor)|Zničí `affinity_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `affinity_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ affinity_partitioner 

 Zničí `affinity_partitioner` objektu.  
  
```
~affinity_partitioner();
```  
  
##  <a name="ctor"></a> affinity_partitioner 

 Vytvoří `affinity_partitioner` objektu.  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
