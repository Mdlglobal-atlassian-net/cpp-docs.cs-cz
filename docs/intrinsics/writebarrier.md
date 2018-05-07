---
title: _Writebarrier – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _WriteBarrier
dev_langs:
- C++
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8197fd38886c887684c3f5f4eb3594088190304d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="writebarrier"></a>_WriteBarrier
**Konkrétní Microsoft**  
  
 Omezení kompilátoru optimalizace, které můžete změnit pořadí operací přístupu k paměti mezi bodem volání.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` vnitřní funkce kompilátoru a `MemoryBarrier` makro jsou všechny zastaralé a by se neměla používat. Pro komunikaci mezi vlákno, použijte mechanismy pro [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md), která jsou definována v [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru, použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru společně s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _WriteBarrier(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_WriteBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_WriteBarrier` Vnitřní omezení kompilátoru optimalizace, které můžete odebrat nebo změnit jeho pořadí operací přístupu k paměti mezi bodem volání.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_ReadBarrier](../intrinsics/readbarrier.md)   
 [_ReadWriteBarrier](../intrinsics/readwritebarrier.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)