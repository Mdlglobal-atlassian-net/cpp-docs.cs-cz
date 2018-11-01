---
title: Upozornění kompilátoru C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6eaaa4c1f16e2ac2c5029511430a145fd9b943e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428337"
---
# <a name="compiler-warning-c4694"></a>Upozornění kompilátoru C4694

> "*třídy*': zapečetěná abstraktní třída nemůže mít je třídou base *$base_class*.

Abstraktní a uzavřené třídy nemůže dědit z typu odkazu uzavřený a abstraktní třída může implementovat funkce základní třídy ani mohl použít jako základní třídu.

Další informace najdete v tématu [abstraktní](../../windows/abstract-cpp-component-extensions.md), [zapečetěné](../../windows/sealed-cpp-component-extensions.md), a [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md).

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```