---
title: Částečné řazení šablon funkcí (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- partial ordering of function templates
ms.assetid: 0c17347d-0e80-47ad-b5ac-046462d9dc73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5b550cd0b76aa0a2e061536ae6bb0ea61063909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46087744"
---
# <a name="partial-ordering-of-function-templates-c"></a>Částečné řazení šablon funkcí (C++)

K dispozici může být několik šablon, které se shodují se seznamem argumentů volání funkce. Jazyk C++ definuje částečné řazení šablon funkcí a určuje tak, která funkce by měla být zavolána. Řazení je částečné, protože mohou existovat šablony považované za shodně specializované.

Kompilátor z možných shod volí nejvíce specializovanou dostupnou šablonu funkce. Například, pokud má typ šablony funkce __T__a jiné funkce šablony trvá __T\*__  je k dispozici, __T\*__  se říká, že verze více specializované a je upřednostňované nad Obecné __T__ verze pokaždé, když argument je typ ukazatele, přestože by být povolená shody.

Chcete-li určit, zda je kandidát šablony funkce více specializovaný, použijte následující postup:

1. Vezměte v úvahu dvě šablony funkcí, T1 a T2.

2. Nahraďte parametry šablony T1 hypotetickým jedinečným typem X.

3. Zjistěte, zda je šablona T2 platnou šablonou pro seznam parametrů šablony T1. Ignorujte všechny implicitní převody.

4. Opakujte stejný postup se záměnou šablon T1 a T2.

5. Je-li jedna šablona platnou šablonou seznamu argumentů pro druhou šablonu, nikoli naopak, je první šablona považována za méně specializovanou než druhá šablona. Je-li obě šablony předchozí krok formuláře platné argumenty pro sebe navzájem, pak jsou považovány za utvářejí a výsledky nejednoznačné volání při pokusu o jejich použití.

6. Použijte tato pravidla:

     1. Specializace šablony pro konkrétní typ je více specializovaná než specializace přijímající argument obecného typu.

     2. Šablony trvá pouze __T\*__  je více specializovaný než jeden trvá __T__, protože typ hypotetické __X\*__  je platným argumentem pro __T__ argument šablony, ale __X__ není platným argumentem pro __T\*__  argument šablony.

     3. __Const T__ je více specializovaný než __T__, protože __const X__ je platným argumentem pro __T__ argument šablony, ale __X__ je argument není platný pro __const T__ argument šablony.

     4. __Const T\*__  je více specializovaný než __T\*__, protože __const X\*__  je platným argumentem pro __T\*__  argument šablony, ale __X\*__  není platným argumentem pro __const T\*__  argument šablony.

## <a name="example"></a>Příklad

Následující příklad funguje dle specifikací standardu:

```cpp
// partial_ordering_of_function_templates.cpp
// compile with: /EHsc
#include <iostream>

extern "C" int printf(const char*,...);
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