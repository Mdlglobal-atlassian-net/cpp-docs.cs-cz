---
title: "Používání setjmp longjmp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs: C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- SETJMPEX.H
- longjmp function in C++ programs
- SETJMP.H
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ac0f4cdbce193c7124a816e4baf5f91e13c71de
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="using-setjmplongjmp"></a>Používání setjmp/longjmp
Když [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) se použijí společně, poskytují způsob, jak provést jiné než místní `goto`. Jsou jsou obvykle používány k předat řízení provádění kódu zpracování chyb nebo obnovení pomocí dříve vyvolání rutiny bez použití standardní volání nebo vrátit konvence.  
  
> [!CAUTION]
>  Ale protože `setjmp` a `longjmp` nepodporují sémantiku C++ objektu a protože tím, že optimalizaci pro místní proměnné se může snížit výkon, doporučujeme používat je v C++ – programy. Doporučujeme vám, že používáte `try` / `catch` vytvoří místo.  
  
 Pokud se rozhodnete použít `setjmp` / `longjmp` v programu C++, také obsahovat SETJMP. H nebo SETJMPEX. H, aby zajistil správnou interakce mezi funkcemi a zpracování výjimek jazyka C++. Pokud používáte [/EH](../build/reference/eh-exception-handling-model.md) zkompilovat, se nazývají destruktory pro místní objekty během unwind zásobníku. Pokud používáte **/EHs** kompilace a jeden z volání funkce a funkce, která používá [nothrow](../cpp/nothrow-cpp.md) a funkce, která používá `nothrow` volání `longjmp`, pak nemusí dojít unwind – destruktor v závislosti na pro optimalizaci.  
  
 V přenosných kódu, pokud nejsou místní `goto` , který volá `longjmp` proveden, může nespolehlivé správné zničení objektů na základě rámce.  
  
## <a name="see-also"></a>Viz také  
 [Kombinování C (strukturované) a výjimky jazyka C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)