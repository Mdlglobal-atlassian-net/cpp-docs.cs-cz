---
title: Chyba kompilátoru C2912
ms.date: 11/04/2016
f1_keywords:
- C2912
helpviewer_keywords:
- C2912
ms.assetid: bd55cecd-ab1a-4636-ab8a-a00393fe7b3d
ms.openlocfilehash: 254252bfd21aa28c87810f1e21b4864e2775a71b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761082"
---
# <a name="compiler-error-c2912"></a>Chyba kompilátoru C2912

deklarace explicitní specializace není specializací šablony funkce.

Nemůžete specializovat funkci, která není šablonou.

Následující ukázka generuje C2912:

```cpp
// C2912.cpp
// compile with: /c
void f(char);
template<> void f(char);   // C2912
template<class T> void f(T);   // OK
```

Tato chyba se taky vygeneruje v důsledku práce s vyhovujícími kompilátory, které se provedly v sadě Visual Studio .NET 2003: pro každou explicitní specializaci musíte zvolit parametry explicitní specializace, třeba to, že odpovídají parametrům primární. vzhledu.

```cpp
// C2912b.cpp
class CF {
public:
   template <class A> CF(const A& a) {}   // primary template

   // attempted explicit specialization
   template <> CF(const char* p) {}   // C2912

   // try the following line instead
   // template <> CF(const char& p) {}
};
```
