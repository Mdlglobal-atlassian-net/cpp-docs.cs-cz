---
title: "_Readbarrier – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- _ReadBarrier
dev_langs:
- C++
helpviewer_keywords:
- _ReadBarrier intrinsic
ms.assetid: f9e54a92-61bc-4f55-8195-b8932065a796
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d76238ed0c3ae66dc153a0a2066d5463a130b859
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="readbarrier"></a>_ReadBarrier  
  
**Microsoft Specific**  
  
 Omezení kompilátoru optimalizace, které můžete změnit pořadí operací přístupu k paměti mezi bodem volání.  
  
> [!CAUTION]
>  `_ReadBarrier`, `_WriteBarrier`, A `_ReadWriteBarrier` vnitřní funkce kompilátoru a `MemoryBarrier` makro jsou všechny zastaralé a by se neměla používat. Pro komunikaci mezi vlákno, použijte mechanismy pro [atomic_thread_fence –](../standard-library/atomic-functions.md#atomic_thread_fence) a [std::atomic\<T >](../standard-library/atomic.md) které jsou definovány v [standardní knihovna C++](../standard-library/cpp-standard-library-reference.md). Pro přístup k hardwaru, použijte [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md) – možnost kompilátoru společně s [volatile](../cpp/volatile-cpp.md) – klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void _ReadBarrier(void);  
```  
  
## <a name="requirements"></a>Požadavky  
  
|Vnitřní funkce|Architektura|  
|---------------|------------------|  
|`_ReadBarrier`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_ReadBarrier` Vnitřní omezení kompilátoru optimalizace, které můžete odebrat nebo změnit jeho pořadí operací přístupu k paměti mezi bodem volání.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)