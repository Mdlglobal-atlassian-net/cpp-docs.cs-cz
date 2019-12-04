---
title: Chyba kompilátoru C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5aa0d27b2d469f53ec521f587172398b7d4c2d1b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761228"
---
# <a name="compiler-error-c2993"></a>Chyba kompilátoru C2993

' identifier ': neplatný typ pro parametr šablony bez typu ' Parameter '

Nelze deklarovat šablonu s argumentem Structure nebo Union. Použijte ukazatele k předání struktur a sjednocení jako parametrů šablony.

Následující ukázka generuje C2993:

```cpp
// C2993.cpp
// compile with: /c
// C2993 expected
struct MyStruct {
   int a;char b;
};

template <class T, struct MyStruct S>   // C2993

// try the following line instead
// template <class T, struct MyStruct * S>
class CMyClass {};
```

Tato chyba se taky vygeneruje v důsledku práce s vyhovujícími kompilátory, které se provedly v sadě Visual Studio .NET 2003: parametry šablony s plovoucí desetinnou čárkou, které nejsou typu, už nejsou povolené. C++ Standard nepovoluje parametry šablony bez typu s plovoucí desetinnou čárkou.

Pokud se jedná o šablonu funkce, použijte argument funkce pro předání v parametru šablony bez typu s plovoucí desetinnou čárkou (Tento kód bude platný v jazyce Visual Studio .NET 2003 a Visual Studio .NET verze vizuálu C++). Pokud se jedná o šablonu třídy, neexistuje jednoduché řešení.

```cpp
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```
