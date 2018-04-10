---
title: tile_barrier – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7d868b4bd677d207590de6449e3d5643001e857
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="tilebarrier-class"></a>tile_barrier – třída
Synchronizuje provádění vláken, která běží ve skupině přístup z více vláken (dlaždice) pomocí `wait` metody. Pouze modul runtime, můžete vytvořit instanci této třídy.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[tile_barrier Constructor](#ctor)|Inicializuje novou instanci třídy `tile_barrier` třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Počkej](#wait)|Dá pokyn všechna vlákna ve skupině přístup z více vláken (dlaždice) má zastavit provádění čekání nedokončili všechna vlákna v dlaždici.|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloky spouštění všechna vlákna v dlaždici dokud byly dokončeny všechny přístupy paměti a všechna vlákna v dlaždici dosáhli toto volání.|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloky provádění všechna vlákna v dlaždici dokud byly dokončeny všechny přístupy globální paměť a všechna vlákna v dlaždici dosáhli toto volání.|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokování provádění všechna vlákna v dlaždici, dokud všechny `tile_static` dokončili přístupů paměti a všechna vlákna v dlaždici dosáhli toto volání.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `tile_barrier`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** amp.h  
  
 **Namespace:** souběžnosti  

## <a name="tile_barrier__ctor"></a>  tile_barrier – konstruktor  
 Inicializuje novou instanci třídy zkopírováním některého ze stávajících.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parametry  
 `_Other`  
 `tile_barrier` Objekt, který chcete kopírovat.  

## <a name="wait"></a>  Počkej 
Dá pokyn všechna vlákna ve skupině přístup z více vláken (dlaždice) Chcete-li zastavit provádění, dokud všechna vlákna v dlaždici čekání na dokončení.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence –   
Bloky provádění všechna vlákna v dlaždici dokud všechna vlákna v dlaždici dosáhli toto volání. To zajistí, že všechny přístupy paměti jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a byly provedeny v programu pořadí.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence   
Bloky provádění všechna vlákna v dlaždici dokud všechna vlákna v dlaždici dosáhli toto volání. To zajistí, že všechny přístupy globální paměť jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a byly provedeny v programu pořadí.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence –   
Bloky provádění všechna vlákna v dlaždici dokud všechna vlákna v dlaždici dosáhli toto volání. To zajistí, že `tile_static` paměti přístupů jsou viditelné pro jiná vlákna v dlaždici přístup z více vláken a byly provedeny v programu pořadí.  
  
### <a name="syntax"></a>Syntaxe 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Viz také  
 [Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
