---
title: Částečné řazení šablon funkcí (C++)
ms.date: 07/30/2019
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
ms.openlocfilehash: 0c4f11b4b3e02504c4786ea34441362b542959d6
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682430"
---
# <a name="partial-ordering-of-function-templates-c"></a>Částečné řazení šablon funkcí (C++)

K dispozici může být několik šablon, které se shodují se seznamem argumentů volání funkce. Jazyk C++ definuje částečné řazení šablon funkcí a určuje tak, která funkce by měla být zavolána. Řazení je částečné, protože mohou existovat šablony považované za shodně specializované.

Kompilátor z možných shod volí nejvíce specializovanou dostupnou šablonu funkce. Například pokud šablona funkce převezme typ `T` a další šablonu funkce `T*` , která je k dispozici, `T*` je verze označována jako specializovaná. Je upřednostňována nad obecnou `T` verzí vždy, když je argumentem typ ukazatele, i když by obě mohly být přípustné shody.

Chcete-li určit, zda je kandidát šablony funkce více specializovaný, použijte následující postup:

1. Vezměte v úvahu dvě šablony funkcí, T1 a T2.

1. Nahraďte parametry šablony T1 hypotetickým jedinečným typem X.

1. Zjistěte, zda je šablona T2 platnou šablonou pro seznam parametrů šablony T1. Ignorujte všechny implicitní převody.

1. Opakujte stejný postup se záměnou šablon T1 a T2.

1. Pokud je jedna šablona platným seznamem argumentů šablony pro druhou šablonu, ale povýšení není true, pak je tato šablona považována za méně specializovanou než druhá šablona. Pokud při použití předchozího kroku obě šablony tvoří platné argumenty navzájem, jsou považovány za stejně specializované a při pokusu o jejich použití nejednoznačné výsledky volání.

1. Použijte tato pravidla:

   1. Specializace šablony pro konkrétní typ je více specializovaná než specializace přijímající argument obecného typu.

   1. Šablona, která přijímá `T*` pouze `T`, je více specializovaná než jedna, protože hypotetický `X*` typ je platným argumentem `T` pro argument šablony, `X` ale není platným argumentem pro `T*`argument šablony

   1. `const T`je více specializovaný než `T`, protože `const X` je platným argumentem pro `T` argument šablony, `const T` ale `X` není platným argumentem pro argument šablony.

   1. `const T*`je více specializovaný než `T*`, protože `const X*` je platným argumentem pro `T*` argument šablony, `const T*` ale `X*` není platným argumentem pro argument šablony.

## <a name="example"></a>Příklad

Následující příklad funguje podle standardu:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

template <class T> void f(T) {
   printf_s("Less specialized function called\n");
}

template <class T> void f(T*) {
   printf_s("More specialized function called\n");
}

template <class T> void f(const T*) {
   printf_s("Even more specialized function for const T*\n");
}

int main() {
   int i =0;
   const int j = 0;
   int *pi = &i;
   const int *cpi = &j;

   f(i);   // Calls less specialized function.
   f(pi);  // Calls more specialized function.
   f(cpi); // Calls even more specialized function.
   // Without partial ordering, these calls would be ambiguous.
}
```

### <a name="output"></a>Výstup

```Output
Less specialized function called
More specialized function called
Even more specialized function for const T*
```

## <a name="see-also"></a>Viz také:

[Šablony funkcí](../cpp/function-templates.md)
