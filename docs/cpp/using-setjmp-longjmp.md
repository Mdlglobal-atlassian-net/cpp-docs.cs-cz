---
title: "Používání setjmp longjmp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- longjmp_cpp
- setjmp_cpp
dev_langs:
- C++
helpviewer_keywords:
- C++ exception handling, setjmp/longjmp functions
- setjmpex.h
- longjmp function in C++ programs
- setjmp.h
- setjmp function
- setjmp function, C++ programs
ms.assetid: 96be8816-f6f4-4567-9a9c-0c3c720e37c5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3fede2e7865ab002d77a174a28928df491b29981
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/25/2018
---
# <a name="using-setjmplongjmp"></a>Používání setjmp/longjmp
Když [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) se použijí společně, poskytují způsob, jak provést jiné než místní `goto`. Jsou jsou obvykle používány k předat řízení provádění kódu zpracování chyb nebo obnovení pomocí dříve vyvolání rutiny bez použití standardní volání nebo vrátit konvence.  
  
> [!CAUTION]
>  Ale protože `setjmp` a `longjmp` nepodporují sémantiku C++ objektu a protože tím, že optimalizaci pro místní proměnné se může snížit výkon, doporučujeme používat je v C++ – programy. Doporučujeme vám, že používáte `try` / `catch` vytvoří místo.  
  
 Pokud se rozhodnete použít `setjmp` / `longjmp` v programu C++, také obsahovat \<setjmp.h > nebo \<setjmpex.h > Chcete-li zajistit správné interakce mezi funkcemi a zpracování výjimek jazyka C++. Pokud používáte [/EH](../build/reference/eh-exception-handling-model.md) zkompilovat, se nazývají destruktory pro místní objekty během unwind zásobníku. Pokud používáte **/EHs** kompilace a jeden z volání funkce a funkce, která používá [nothrow](../cpp/nothrow-cpp.md) a funkce, která používá `nothrow` volání `longjmp`, pak nemusí dojít unwind – destruktor v závislosti na pro optimalizaci.  
  
 V přenosných kódu, pokud nejsou místní `goto` , který volá `longjmp` proveden, může nespolehlivé správné zničení objektů na základě rámce.  
  
## <a name="see-also"></a>Viz také  
 [Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)