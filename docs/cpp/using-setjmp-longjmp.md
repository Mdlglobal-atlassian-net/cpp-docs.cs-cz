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
ms.openlocfilehash: 2073729fc5445fc36e3d8a6f52c4f69b079c8b47
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462128"
---
# <a name="using-setjmplongjmp"></a>Používání setjmp/longjmp
Když [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) se použijí společně, poskytují způsob provedení nemístního **goto**. Jsou obvykle slouží k předání ovládacího prvku spuštění pro zpracování chyb nebo kódu obnovení v dříve volané rutině bez použití standardní volání nebo vrácení konvence.  
  
> [!CAUTION]
>  Ale protože **setjmp** a **longjmp** nepodporují sémantiku objektu C++ a vzhledem k tomu, že se může snížit výkon tím, že zabrání optimalizaci na lokálních proměnných, doporučujeme je velmi riskantní používat je v programech jazyka C++. Doporučujeme, abyste použili **zkuste**/**catch** místo toho vytvoří.  
  
 Pokud se rozhodnete použít **setjmp**/**longjmp** v programu v jazyce C++, také zahrnovat \<setjmp.h > nebo \<setjmpex.h > pro zajištění správné interakci mezi Funkce a zpracování výjimek jazyka C++. Pokud používáte [/EH](../build/reference/eh-exception-handling-model.md) ke kompilaci, destruktory pro místní objekty jsou volány během zásobníku unwind. Pokud používáte **/EHS** pro kompilaci a jedna z funkcí volá funkci, která používá [nothrow](../cpp/nothrow-cpp.md) a funkci, která používá **nothrow** volání **longjmp**, pak destruktor unwind nemusí vzniknout v závislosti optimalizaci.  
  
 V přenositelném kódu, když jiné než místní **goto** , která volá **longjmp** provádí, správná destrukce objektů založených na snímcích, může nespolehlivá.  
  
## <a name="see-also"></a>Viz také:  
 [Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)