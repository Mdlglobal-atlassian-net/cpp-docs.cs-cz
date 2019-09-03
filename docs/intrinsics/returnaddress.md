---
title: _ReturnAddress
ms.date: 09/02/2019
f1_keywords:
- _ReturnAddress
helpviewer_keywords:
- _ReturnAddress intrinsic
- ReturnAddress intrinsic
ms.assetid: 7f4a5811-35e6-4f64-ba7c-21203380eeda
ms.openlocfilehash: 2a830ff1e8a2c9551dec52cf10a3d5cf126bde3b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218056"
---
# <a name="_returnaddress"></a>_ReturnAddress

**Specifické pro společnost Microsoft**

`_ReturnAddress` Vnitřní poskytuje adresu instrukcí ve funkci volání, která bude provedena po návratu ovládacího prvku volajícímu.

Sestavte následující program a proveďte jeho krok v ladicím programu. Při procházení programu si poznamenejte adresu, která je vrácena z `_ReturnAddress`. Potom hned po návratu z funkce, kde `_ReturnAddress` byla použita, [otevřete postup: Použijte okno](/visualstudio/debugger/how-to-use-the-disassembly-window) zpětný překlad a Všimněte si, že adresa další instrukce, která se má provést, se shoduje s adresou `_ReturnAddress`vrácenou z.

Tato zpáteční adresa může mít vliv na optimalizace, jako je například vkládání. Například pokud je ukázkový program kompilován pomocí [/OB1](../build/reference/ob-inline-function-expansion.md), `inline_func` bude vložen do volání funkce, `main`. Proto volání `_ReturnAddress` z `inline_func` a `main` budou každé vracet stejnou hodnotu.

Při `_ReturnAddress` použití v programu zkompilovaném pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md)bude funkce obsahující `_ReturnAddress` volání zkompilována jako nativní funkce. Pokud je funkce kompilována jako spravovaná volání do funkce obsahující `_ReturnAddress`, `_ReturnAddress` nemusí chovat podle očekávání.

## <a name="requirements"></a>Požadavky

**Hlavičkový soubor** \<intrin. h >

## <a name="example"></a>Příklad

```cpp
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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[_AddressOfReturnAddress](../intrinsics/addressofreturnaddress.md)\
[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[Klíčová slova](../cpp/keywords-cpp.md)
