---
title: Pravidla a omezení pro holé funkce
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: ec5c7d635dbbb63af7177395c5ad08356e1a26f0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857304"
---
# <a name="rules-and-limitations-for-naked-functions"></a>Pravidla a omezení pro holé funkce

**Specifické pro společnost Microsoft**

Na neviditelné funkce se vztahují následující pravidla a omezení:

- Příkaz **return** není povolen.

- Konstrukce strukturovaného zpracování výjimek a zpracování výjimek jazyka C++ nejsou povoleny, protože se musejí odvíjet prostřednictvím rámce zásobníku.

- Ze stejného důvodu je zakázána jakákoli forma `setjmp`.

- Použití funkce `_alloca` je zakázáno.

- Pro ujištění, že se před sekvencí prologu neobjeví žádná inicializace kódu lokálních proměnných, nejsou v rámci oboru funkce povoleny inicializované místní proměnné. Konkrétně není v oboru funkce povolena deklarace objektů jazyka C++. Ve vnořeném oboru se však mohou vyskytovat inicializovaná data.

- Optimalizace ukazatele rámce (možnost kompilátoru /Oy) se nedoporučuje, ale je u neviditelné funkce automaticky potlačena.

- V rámci oboru lexikální funkce nelze deklarovat třídu objektů jazyka C++. Objekty lze však deklarovat ve vnořeném bloku.

- Klíčové slovo **holé** se při kompilaci s možností [/CLR](../build/reference/clr-common-language-runtime-compilation.md)ignoruje.

- Pro [__fastcall](../cpp/fastcall.md) holé funkce, vždy, když existuje odkaz v kódu CC++ /Code k jednomu z argumentů registru, kód prologu by měl ukládat hodnoty daného registru do umístění zásobníku pro tuto proměnnou. Příklad:

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

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Volání holé funkce](../cpp/naked-function-calls.md)