---
title: Kompilátor upozornění (úroveň 4) C4754
ms.date: 11/04/2016
f1_keywords:
- C4754
helpviewer_keywords:
- C4754
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
ms.openlocfilehash: 6ce6886c74a2a82a2a072a3f5d7e3222bb572bea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477373"
---
# <a name="compiler-warning-level-4-c4754"></a>Kompilátor upozornění (úroveň 4) C4754

Pravidla převodu pro aritmetické operace v porovnání se rozumí, že jednu větev nejde provést.

Objeví se upozornění C4754, protože výsledkem porovnání je vždy stejný. To znamená, že jeden z větve podmínka není nikdy proveden, pravděpodobně protože přidružené celočíselný výraz není správná. Tato vada kódu často dochází v kontroly přetečení celých nesprávné na 64bitové architektury.

Pravidla převodu celého čísla jsou komplexní a existuje mnoho drobným nástrahy. Jako alternativu k opravě každý C4754 upozornění, můžete aktualizovat kód, který použije [SafeInt – knihovna](../../windows/safeint-library.md).

## <a name="example"></a>Příklad

Tato ukázka vygeneruje C4754:

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

Přidání `a + b` předtím, než je přetypování nahoru na 64 bitů hodnotu výsledku by mohlo způsobit aritmetické přetečení a přiřazená k proměnné 64-bit `x`. To znamená, že kontrola `x` je redundantní a nikdy catch přetečení. V tomto případě kompilátor vydá toto varování:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754a.cpp (7) mean that one branch cannot be executed. Cast '(a + ...)' to 'ULONG64' (or similar type of 8 bytes).
```

Chcete-li upozornění odstranit, můžete změnit příkazu přiřazení k přetypování operandy na 8 bajtů hodnoty:

```cpp
// Casting one operand is sufficient to force all the operands in
// the addition be upcast according to C/C++ conversion rules, but
// casting both is clearer.
unsigned long long x =
   (unsigned long long)a + (unsigned long long)b;
```

## <a name="example"></a>Příklad

Následující ukázka generuje také C4754.

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

`sizeof()` Operátor vrátí `size_t`, jejíž velikost je závislé na architekturu. Ukázkový kód funguje na 32bitové architektury kde `size_t` je typem 32-bit. Ale na 64bitové architektury `size_t` je 64bitového typu. Pravidla převodu pro celá čísla znamenají, že `a` je přetypování nahoru na 64 bitů hodnotu ve výrazu `a + b < a` jakoby byly napsány `(size_t)a + (size_t)b < (size_t)a`. Když `a` a `b` jsou 32bitová celá čísla, nikdy přetečení operace sčítání 64bitovým kompilátorem a omezení nikdy neudržuje. V důsledku toho kód nikdy zjistí přetečení celého čísla na 64bitové architektury. Tento příklad způsobí, že kompilátor generuje toto upozornění:

```Output
Warning C4754: Conversion rules for arithmetic operations in the comparison at C4754b.cpp (7) mean that one branch cannot be executed. Cast '4' to 'ULONG' (or similar type of 4 bytes).
```

Všimněte si, že upozornění explicitně obsahuje konstantní hodnotu 4 namísto původní zdrojový řetězec – době upozornění analýzy zaznamená problematický kód `sizeof(unsigned long)` již byl převeden na konstantu. Proto bude pravděpodobně nutné sledovat dolů výrazu, který ve zdrojovém kódu souvisí s konstantní hodnotou v upozornění. Nejběžnějšími zdroji kód přeložit konstanty v C4754 varovné zprávy, jako jsou výrazy `sizeof(TYPE)` a `strlen(szConstantString)`.

Oprava kódu v tomto případě by vypadat takto:

```cpp
// Casting the result of sizeof() to unsigned long ensures
// that all the addition operands are 32-bit, so any overflow
// is detected by the check.
if (a + (unsigned long)sizeof(unsigned long) < a)

```

**Poznámka:** uvedená v upozornění kompilátoru číslo řádku je poslední řádek příkazu. Ve zprávě s upozorněním o komplexní podmíněném příkazu, která je rozdělena do více řádků řádek, který je závadný kód může být Víceřádkový před řádek, který se použije v hlášení. Příklad:

```cpp
unsigned long a;

if (a + sizeof(unsigned long) < a || // incorrect check
    condition1() ||
    a == 0) {    // C4754 warning reported on this line
         // never executes!
         return INVALID_PARAMETER;
}
```