---
title: "simple_partitioner – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
dev_langs: C++
helpviewer_keywords: simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f1d509afd9cddd8ac119d12ce2a0cb88906e83aa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
|[~ simple_partitioner – destruktor](#dtor)|Zničí `simple_partitioner` objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `simple_partitioner`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ppl.h  
  
 **Namespace:** souběžnosti  
  
##  <a name="dtor"></a>~ simple_partitioner 

 Zničí `simple_partitioner` objektu.  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a>simple_partitioner 

 Vytvoří `simple_partitioner` objektu.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parametry  
 `_Chunk_size`  
  
## <a name="see-also"></a>Viz také  
 [concurrency – obor názvů](concurrency-namespace.md)
