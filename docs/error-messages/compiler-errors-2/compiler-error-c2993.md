---
title: Chyba kompilátoru C2993 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2993
dev_langs:
- C++
helpviewer_keywords:
- C2993
ms.assetid: 4ffd2b78-654b-46aa-95a6-b62101cf91c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09b3c789cc15d2e146f1c5031003fc74d783e827
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081935"
---
# <a name="compiler-error-c2993"></a>Chyba kompilátoru C2993

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