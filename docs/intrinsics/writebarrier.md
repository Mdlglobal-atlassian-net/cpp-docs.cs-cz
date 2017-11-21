---
title: "_Writebarrier – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _WriteBarrier
dev_langs: C++
helpviewer_keywords:
- WriteBarrier intrinsic
- _WriteBarrier intrinsic
ms.assetid: a5ffdad9-0ca1-4eb7-b2f3-0f092c4bf4b5
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 33644d332a83f1bb80f6812f04daefb227fd8a65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
|`_WriteBarrier`|x86,[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Soubor hlaviček** \<intrin.h >  
  
## <a name="remarks"></a>Poznámky  
 `_WriteBarrier` Vnitřní omezení kompilátoru optimalizace, které můžete odebrat nebo změnit jeho pořadí operací přístupu k paměti mezi bodem volání.  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [_Readbarrier –](../intrinsics/readbarrier.md)   
 [_Readwritebarrier –](../intrinsics/readwritebarrier.md)   
 [Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)