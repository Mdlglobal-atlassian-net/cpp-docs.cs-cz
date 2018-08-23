---
title: Použití funkcí setjmp a longjmp | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: a83253fb98506bb586af2b52ef3321bada7ca01f
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2018
ms.locfileid: "42464632"
---
# <a name="using-setjmp-and-longjmp"></a>Použití funkcí setjmp a longjmp

Když [setjmp](../c-runtime-library/reference/setjmp.md) a [longjmp](../c-runtime-library/reference/longjmp.md) se použijí společně, poskytují způsob provedení nemístního **goto**. Jsou se obvykle používají v kódu jazyka C k předání ovládacího prvku spuštění pro zpracování chyb nebo kódu obnovení v dříve volané rutině bez použití standardní volání nebo vrácení konvence.

> [!CAUTION]
> Protože `setjmp` a `longjmp` nepodporují správná destrukce objektů rámce zásobníku přenositelnosti mezi kompilátory jazyka C++ a vzhledem k tomu, že se může snížit výkon tím, že zabrání optimalizaci na lokálních proměnných, nedoporučujeme jejich použití v jazyce C++ programy. Doporučujeme použít **zkuste** a **catch** místo toho vytvoří.

Pokud se rozhodnete použít `setjmp` a `longjmp` v programu v jazyce C++, také zahrnovat \<setjmp.h > nebo \<setjmpex.h > pro zajištění správné interakci mezi funkcemi a výjimky strukturovaného zpracování výjimek (SEH) nebo C++ zpracování.

**Specifické pro Microsoft**

Pokud používáte [/EH](../build/reference/eh-exception-handling-model.md) umožňuje kompilaci kódu jazyka C++, destruktory pro místní objekty jsou volány během zásobníku unwind. Nicméně pokud používáte **/EHS** nebo **/EHsc** pro kompilaci a jedna z funkcí, která používá [noexcept](../cpp/noexcept-cpp.md) volání `longjmp`, pak destruktor unwind pro tuto funkci nemusí vzniknout v závislosti na stavu optimalizace.

V přenositelném kódu když `longjmp` zpracovává volání, správná destrukce objektů založených na snímcích je explicitně není zaručeno, Standard a nemusí být podporované jinými kompilátory. S oznámením na úroveň upozornění 4, volání `setjmp` způsobí upozornění C4611: interakce mezi "_setjmp" a destrukcí objektu C++ není typu portable.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Kombinace výjimek v jazycích C (strukturované) a C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)  
