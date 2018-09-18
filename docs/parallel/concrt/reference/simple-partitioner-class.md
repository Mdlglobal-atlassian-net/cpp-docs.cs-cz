---
title: simple_partitioner – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 98c4c82bcf858215ceba31e2ddd0770511446f72
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46075641"
---
# <a name="simplepartitioner-class"></a>simple_partitioner – třída
`simple_partitioner` Třída reprezentuje statické dělení provést iteraci přes podle rozsahu `parallel_for`. Dělicí rozsahu rozdělí do bloků dat tak, aby měl každý blok minimální počet iterací určená velikost deduplikačního bloku dat.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[simple_partitioner](#ctor)|Vytvoří `simple_partitioner` objektu.|  
|[~simple_partitioner Destructor](#dtor)|Odstraní `simple_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `simple_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a> ~ simple_partitioner – 

 Odstraní `simple_partitioner` objektu.  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a> simple_partitioner – 

 Vytvoří `simple_partitioner` objektu.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parametry  
*_Chunk_size*<br/>
Požadovanou minimální velikost oddílu.
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
