---
title: _ReturnAddress
ms.date: 11/04/2016
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 01916a9306faa4159f54225b745fd56c35b5ae16
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641780"
---
# <a name="returnaddress"></a>_ReturnAddress

## <a name="microsoft-specific"></a>Specifické pro Microsoft

`_ReturnAddress` Vnitřní poskytuje adresu podle pokynů ve volání funkce, která se spustí po ovládací prvek vrátí volajícímu.

Vytvářejte následující program a procházet ji krok v ladicím programu. Jak krokovat programem, poznamenejte si adresu, která je vrácena z `_ReturnAddress`. Potom ihned po vrácení z funkce kde `_ReturnAddress` byl použit, otevřete [postupy: použití okna zpětného překladu](/visualstudio/debugger/how-to-use-the-disassembly-window) a Všimněte si, že adresa má být proveden další pokyn odpovídá adrese vrácená `_ReturnAddress`.

Optimalizace, například vkládání může mít vliv na návratovou adresu. Například, pokud je uvedený ukázkový program kompilován [/Ob1](../build/reference/ob-inline-function-expansion.md), `inline_func` budou vloženy do volání funkce `main`. Proto volání `_ReturnAddress` z `inline_func` a `main` bude každý vytváří stejnou hodnotu.

Když `_ReturnAddress` se používá v programu kompilovaného s [/CLR](../build/reference/clr-common-language-runtime-compilation.md), funkce obsahující `_ReturnAddress` volání se zkompilovat jako nativní funkce. Když funkci zkompilovat jako spravovaná volání do funkce obsahující `_ReturnAddress`, `_ReturnAddress` nemusí chovat dle očekávání.

## <a name="requirements"></a>Požadavky

**Soubor hlaviček** \<intrin.h >

## <a name="example"></a>Příklad

```
// compiler_intrinsics__ReturnAddress.cpp
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_ReturnAddress)

__declspec(noinline)
void noinline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

__forceinline
void inline_func(void)
{
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());
}

int main(void)
{
   noinline_func();
   inline_func();
   printf("Return address from %s: %p\n", __FUNCTION__, _ReturnAddress());

   return 0;
}
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)<br/>
[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)