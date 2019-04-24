---
title: Chyba kompilátoru C2244
ms.date: 11/04/2016
f1_keywords:
- C2244
helpviewer_keywords:
- C2244
ms.assetid: d9911c12-ceb5-4f93-ac47-b44a485215c2
ms.openlocfilehash: 7cfa0cd7ff4290ca5f07fb712bbcac7dabf55f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301393"
---
# <a name="compiler-error-c2244"></a>Chyba kompilátoru C2244

'identifier': nejde namapovat definici funkce na existující deklaraci

Neobvyklé použití unární + – operátor byl použit před volání funkce, které nemají závorky.

K této chybě dochází pouze v projektech C++.

Následující ukázka generuje C2244:

```
// C2244.cpp
int func(char) {
   return 0;
}

int func(int) {
   return 0;
}

int main() {
   +func;   // C2244
}
```

C2244 může vzniknout také při použití podpis nesprávná funkce pro členské funkce třídy šablony.

```
// C2244b.cpp
// compile with: /c
template<class T>
class XYZ {
   void func(T t);
};

template<class T>
void XYZ<T>::func(int i) {}   // C2244 wrong function signature
// try the following line instead
// void XYZ<T>::func(T t) {}
```

C2244 může dojít, když se podpis nesprávná funkce používá šablony členské funkce.

```
// C2244c.cpp
// compile with: /c
class ABC {
   template<class T>
   void func(int i, T t);
};

template<class T>
void ABC::func(int i) {}   // C2244 wrong signature
// try the following line instead
// void ABC::func(int i, T t) {}
```

Nelze částečně specializovat šablonu funkce.

```
// C2244d.cpp
template<class T, class U>
class QRS {
   void func(T t, U u);
};

template<class T>
void QRS<T,int>::func(T t, int u) {}   // C2244
```