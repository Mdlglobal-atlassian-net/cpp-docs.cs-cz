---
title: Použití funkcí setjmp/longjmp | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f68cd13304e73282735ad1227510b289b19caed8
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37939764"
---
# <a name="using-setjmplongjmp"></a>Používání setjmp/longjmp
Když [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) se použijí společně, poskytují způsob provedení nemístního **goto**. Jsou obvykle slouží k předání ovládacího prvku spuštění pro zpracování chyb nebo kódu obnovení v dříve volané rutině bez použití standardní volání nebo vrácení konvence.  
  
> [!CAUTION]
>  Ale protože `setjmp` a `longjmp` nepodporují sémantiku objektu C++ a vzhledem k tomu, že se může snížit výkon tím, že zabrání optimalizaci na lokálních proměnných, doporučujeme je velmi riskantní používat je v programech jazyka C++. Doporučujeme, abyste použili **zkuste**/**catch** místo toho vytvoří.  
  
 Pokud se rozhodnete použít `setjmp` / `longjmp` v programu v jazyce C++, také zahrnovat \<setjmp.h > nebo \<setjmpex.h > pro zajištění správné interakci mezi funkcemi a zpracování výjimek jazyka C++. Pokud používáte [/EH](../build/reference/eh-exception-handling-model.md) ke kompilaci, destruktory pro místní objekty jsou volány během zásobníku unwind. Pokud používáte **/EHS** pro kompilaci a jedna z funkcí volá funkci, která používá [nothrow](../cpp/nothrow-cpp.md) a funkci, která používá **nothrow** volání `longjmp`, pak bude destruktor unwind nemusí vzniknout v závislosti optimalizaci.  
  
 V přenositelném kódu, když jiné než místní **goto** , která volá `longjmp` provádí, správná destrukce objektů založených na snímcích, může nespolehlivá.  
  
## <a name="see-also"></a>Viz také  
 [Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)