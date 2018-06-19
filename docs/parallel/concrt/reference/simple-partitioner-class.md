---
title: simple_partitioner – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3ef53ed9fa69dc77c93b90f9f24fa8628d589b07
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705260"
---
# <a name="simplepartitioner-class"></a>simple_partitioner – třída
`simple_partitioner` Třída reprezentuje statické dělení vstupní přes podle rozsahu `parallel_for`. Dělicí metody rozsahu rozdělí do bloků, tak, aby měl každého bloku alespoň počet iterací určeného velikost bloku.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[simple_partitioner](#ctor)|Vytvoří `simple_partitioner` objektu.|  
|[~simple_partitioner Destructor](#dtor)|Zničí `simple_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `simple_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ simple_partitioner 

 Zničí `simple_partitioner` objektu.  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a> simple_partitioner 

 Vytvoří `simple_partitioner` objektu.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parametry  
 `_Chunk_size`  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
