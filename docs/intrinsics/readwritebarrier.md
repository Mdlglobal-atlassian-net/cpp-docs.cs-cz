---
title: "_Readwritebarrier – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _ReadWriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- ReadWriteBarrier intrinsic
- _ReadWriteBarrier intrinsic
ms.assetid: dd9f58b5-8bb6-494e-bb0f-9fe184f3908d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: acc177ad5f98405571a418f849d35fa98242e0f2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="readwritebarrier"></a>_ReadWriteBarrier
**Microsoft Specific**  
  
 Omezení kompilátoru optimalizace, které můžete změnit pořadí přístupů paměti mezi bodem volání.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` vnitřní funkce kompilátoru a `MemoryBarrier` makro jsou všechny zastaralé a by se neměla používat. Pro komunikaci mezi vlákno, použijte mechanismy pro [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md), která jsou definována v [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru, použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru společně s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _ReadWriteBarrier(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_ReadWriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_ReadWriteBarrier` Vnitřní omezení kompilátoru optimalizace, které můžete odebrat nebo změnit jeho pořadí přístupů paměti mezi bodem volání.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_WriteBarrier](../intrinsics/writebarrier.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)