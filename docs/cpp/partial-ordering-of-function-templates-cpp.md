---
title: Částečné řazení šablon funkcí (C++) | Microsoft Docs
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
ms.openlocfilehash: 60936a46732e4b2ed827a5efb08740661d9bb0d9
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="partial-ordering-of-function-templates-c"></a>Částečné řazení šablon funkcí (C++)

K dispozici může být několik šablon, které se shodují se seznamem argumentů volání funkce. Jazyk C++ definuje částečné řazení šablon funkcí a určuje tak, která funkce by měla být zavolána. Řazení je částečné, protože mohou existovat šablony považované za shodně specializované.

Kompilátor z možných shod volí nejvíce specializovanou dostupnou šablonu funkce. Například, pokud šablonu funkce trvá typu __T__a jinou šablonu funkce trvá __T\*__  je k dispozici, __T\*__  je uvedená verze více specializuje a je upřednostňovaný nad obecná __T__ verze vždy, když argument je ukazatel typu, i když obě by být povolené odpovídá.

Chcete-li určit, zda je kandidát šablony funkce více specializovaný, použijte následující postup:

1. Vezměte v úvahu dvě šablony funkcí, T1 a T2.

2. Nahraďte parametry šablony T1 hypotetickým jedinečným typem X.

3. Zjistěte, zda je šablona T2 platnou šablonou pro seznam parametrů šablony T1. Ignorujte všechny implicitní převody.

4. Opakujte stejný postup se záměnou šablon T1 a T2.

5. Je-li jedna šablona platnou šablonou seznamu argumentů pro druhou šablonu, nikoli naopak, je první šablona považována za méně specializovanou než druhá šablona. Pokud obě šablony pomocí předchozího kroku formuláře platné argumenty pro sebe navzájem, pak jsou považovány za stejnou měrou se specializuje a nejednoznačné volání výsledků, při pokusu jejich použití.

6. Použijte tato pravidla:

     1. Specializace šablony pro konkrétní typ je více specializovaná než specializace přijímající argument obecného typu.

     2. Šablony trvá pouze __T\*__  je specializované více než jeden trvá __T__, protože typ hypotetický __X\*__  je platný argument pro __T__ argument šablony, ale __X__ není platným argumentem pro __T\*__  argument šablony.

     3. __Const T__ je specializované více než __T__, protože __const X__ je platný argument pro __T__ argument šablony, ale __X__ je není platný argument pro __const T__ argument šablony.

     4. __Const T\*__  je specializované více než __T\*__, protože __const X\*__  je platný argument pro __T\*__  argument šablony, ale __X\*__  není platným argumentem pro __const T\*__  argument šablony.

## <a name="example"></a>Příklad

Následující ukázka funguje jako zadaný v standardní:

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
  
```  
Less specialized function called  
More specialized function called  
Even more specialized function for const T*  
```  
  
## <a name="see-also"></a>Viz také

[Šablony funkcí](../cpp/function-templates.md)
