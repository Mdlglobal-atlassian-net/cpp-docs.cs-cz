---
title: Pravidla a omezení pro holé funkce
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: c813b97b85469165aae892b0a4cce888112e3dc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267369"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Pravidla a omezení pro holé funkce

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Na neviditelné funkce se vztahují následující pravidla a omezení:

- **Vrátit** příkazu není povolený.

- Konstrukce strukturovaného zpracování výjimek a zpracování výjimek jazyka C++ nejsou povoleny, protože se musejí odvíjet prostřednictvím rámce zásobníku.

- Ze stejného důvodu je zakázána jakákoli forma `setjmp`.

- Použití funkce `_alloca` je zakázáno.

- Pro ujištění, že se před sekvencí prologu neobjeví žádná inicializace kódu lokálních proměnných, nejsou v rámci oboru funkce povoleny inicializované místní proměnné. Konkrétně není v oboru funkce povolena deklarace objektů jazyka C++. Ve vnořeném oboru se však mohou vyskytovat inicializovaná data.

- Optimalizace ukazatele rámce (možnost kompilátoru /Oy) se nedoporučuje, ale je u neviditelné funkce automaticky potlačena.

- V rámci oboru lexikální funkce nelze deklarovat třídu objektů jazyka C++. Objekty lze však deklarovat ve vnořeném bloku.

- **Naked** – klíčové slovo je ignorována při kompilaci s [/CLR](../build/reference/clr-common-language-runtime-compilation.md).

- Pro [__fastcall](../cpp/fastcall.md) nahé funkce, vždycky, když je odkaz v jazyce C /C++ kódu do jednoho z argumentů registru by měl kód prologu uložit hodnoty daného registru do umístění zásobníku pro danou proměnnou. Příklad:

```cpp
// nkdfastcl.cpp
// compile with: /c
// processor: x86
__declspec(naked) int __fastcall  power(int i, int j) {
   // calculates i^j, assumes that j >= 0

   // prolog
   __asm {
      push ebp
      mov ebp, esp
      sub esp, __LOCAL_SIZE
     // store ECX and EDX into stack locations allocated for i and j
     mov i, ecx
     mov j, edx
   }

   {
      int k = 1;   // return value
      while (j-- > 0)
         k *= i;
      __asm {
         mov eax, k
      };
   }

   // epilog
   __asm {
      mov esp, ebp
      pop ebp
      ret
   }
}
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Volání holé funkce](../cpp/naked-function-calls.md)