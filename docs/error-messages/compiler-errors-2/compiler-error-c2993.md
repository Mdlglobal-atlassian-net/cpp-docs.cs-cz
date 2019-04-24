---
title: Compiler Error C2993
ms.date: 11/04/2016
f1_keywords:
- C2993
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
ms.openlocfilehash: 5be4836332f67f2064f60a3b058db159a18ca1e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160884"
---
# <a name="compiler-error-c2993"></a>Compiler Error C2993

'identifier': Neplatný typ pro parametr šablony bez typu 'parametr'

Šablona s struktury nebo sjednocení argument nelze deklarovat. Použijte ukazatele k předávání struktur a sjednocení jako parametry šablony.

Následující ukázka generuje C2993:

```
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

K této chybě také se vygeneruje jako výsledek kompilátoru prací, které bylo provedeno v aplikaci Visual Studio .NET 2003: již není povolena parametry šablony bez typu s plovoucí desetinnou čárkou. C++ standard nepovoluje parametry šablony bez typu s plovoucí desetinnou čárkou.

Pokud je funkce šablony, použijte argument funkce a zajistěte tak předání plovoucí bodu parametr šablony bez typu (Tento kód bude platit ve Visual Studio .NET 2003 a Visual Studio .NET verzí jazyka Visual C++). Pokud je šablona třídy, neexistuje žádné alternativní řešení snadno.

```
// C2993b.cpp
// compile with: /c
template<class T, float f> void func(T) {}   // C2993

// OK
template<class T>   void func2(T, float) {}
```