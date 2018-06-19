---
title: affinity_partitioner – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2242346bda717117e2b43ba108d86fd2a77a3b58
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691128"
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
|[~ affinity_partitioner – destruktor](#dtor)|Zničí `affinity_partitioner` objektu.|  
  
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
