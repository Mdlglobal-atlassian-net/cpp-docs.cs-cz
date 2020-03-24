---
title: Upozornění kompilátoru (úroveň 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: f55d40044fef58275ad0e1fbd281b5f1af43c243
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198130"
---
# <a name="compiler-warning-level-4-c4754"></a>Upozornění kompilátoru (úroveň 4) C4754

Pravidla převodu pro aritmetické operace v porovnání znamenají, že jednu větev nelze provést.

Upozornění C4754 je vystaveno, protože výsledek porovnání je vždy stejný. To znamená, že jedna z větví podmínky není nikdy provedena, pravděpodobně proto, že přidružený celočíselný výraz není správný. Tato vada kódu často probíhá v nesprávných kontrolách přetečení celých čísel v 64 bitových architekturách.

Pravidla převodu celého čísla jsou složitá a existuje mnoho drobných nástrah. Jako alternativu k opravě každého upozornění C4754 můžete kód aktualizovat tak, aby používal [knihovnu SafeInt](../../safeint/safeint-library.md).

## <a name="example"></a>Příklad

Tato ukázka generuje C4754:

```cpp
// C4754a.cpp
// Compile with: /W4 /c
#include "errno.h"

int sum_overflow(unsigned long a, unsigned long b)
{
   unsigned long long x = a + b; // C4754

   if (x > 0xFFFFFFFF)
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

`a + b` sčítání by mohlo způsobit přetečení aritmetické operace před tím, než je výsledek převeden na 64ovou hodnotu a přiřazeno k proměnné 64-bit `x`. To znamená, že `x` kontrole je redundantní a nebude nikdy zachytit přetečení. V tomto případě kompilátor vygeneruje toto upozornění:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

Chcete-li odstranit upozornění, můžete změnit příkaz přiřazení pro přetypování operandů na 8bitové hodnoty:

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

## <a name="example"></a>Příklad

Další ukázka také generuje C4754.

```cpp
// C4754b.cpp
// Compile with: /W4 /c
#include "errno.h"

int wrap_overflow(unsigned long a)
{
   if (a + sizeof(unsigned long) < a) // C4754
   {
      // never executes!
      return EOVERFLOW;
   }
   return 0;
}
```

Operátor `sizeof()` vrátí `size_t`, jehož velikost je závislá na architektuře. Vzorový kód funguje v 32ch architekturách, kde `size_t` je 32-bit typu. Nicméně v 64ch architekturách `size_t` je 64 typ. Pravidla převodu pro celá čísla znamenají, že `a` je přetypování na 64ovou hodnotu ve výrazu `a + b < a`, jako kdyby byla napsána `(size_t)a + (size_t)b < (size_t)a`. Když `a` a `b` jsou 32 celých čísel, operace sčítání 64 nemůže nikdy přetečení a omezení nikdy nedrží. V důsledku toho kód nikdy nezjistí podmínku přetečení celého čísla na 64 bitových architekturách. Tento příklad způsobí, že kompilátor vygeneruje toto upozornění:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

Všimněte si, že zpráva s upozorněním explicitně vypíše konstantní hodnotu 4 namísto původního zdrojového řetězce – v době, kdy při analýze výstrahy dojde k problematickému kódu, `sizeof(unsigned long)` již byl převeden na konstantu. Proto může být nutné sledovat, který výraz ve zdrojovém kódu je přidružen k hodnotě konstanty ve zprávě upozornění. Nejběžnější zdroje kódu se přeložily na konstanty ve zprávách upozornění C4754 jsou výrazy, jako `sizeof(TYPE)` a `strlen(szConstantString)`.

V tomto případě by pevný kód vypadal takto:

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)
```

**Poznámka:** Číslo řádku uvedené v upozorněních kompilátoru je poslední řádek příkazu. Ve zprávě s upozorněním na komplexní podmíněný příkaz, který je rozložen na více řádků, může být řádek, který má vadu kódu, několik řádků před nahlášeným řádkem. Příklad:

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```
