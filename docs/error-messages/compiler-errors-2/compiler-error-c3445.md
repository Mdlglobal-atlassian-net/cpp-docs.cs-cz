---
title: Chyba kompilátoru C3445
ms.date: 04/10/2017
f1_keywords:
- C3445
helpviewer_keywords:
- C3445
ms.assetid: 0d272bfc-136b-4025-a9ba-5e4eea5f8215
ms.openlocfilehash: 2eddeb5a56c953ca0864e29187fbe28c53bdee24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328641"
---
# <a name="compiler-error-c3445"></a>Chyba kompilátoru C3445

> kopírování Inicializace seznamu z "*typ*' nelze použít explicitní konstruktor

Podle ISO standardu C ++ 17 kompilátor je potřeba vzít v úvahu explicitní konstruktor pro řešení přetížení v Inicializace kopírování seznamu, ale musí vyvolat chybu, pokud je ve skutečnosti zvolená tohoto přetížení.

Spouští se v sadě Visual Studio 2017, kompilátor zjistí chyby týkající se vytvoření objektu pomocí seznamu inicializátorů, které nebyly nalezeny ve Visual Studio 2015. K těmto chybám může vést k selhání nebo nedefinované chování za běhu.

## <a name="example"></a>Příklad

Následující ukázka generuje C3445.

```cpp
// C3445.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 };     // error C3445: copy-list-initialization of
                      //     'A' cannot use an explicit constructor
}
```

Chcete-li opravit chybu, použijte přímé inicializace:

```cpp
// C3445b.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1{ 1 };
}
```
