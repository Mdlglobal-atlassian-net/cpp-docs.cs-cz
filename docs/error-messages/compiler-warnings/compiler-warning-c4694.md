---
title: Upozornění kompilátoru C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165116"
---
# <a name="compiler-warning-c4694"></a>Upozornění kompilátoru C4694

> '*Class*': zapečetěná abstraktní třída nemůže mít základní třídu '*BASE_CLASS*'

Abstraktní a zapečetěná třída nemůže dědit z typu odkazu; zapečetěná a abstraktní třída nemůže implementovat funkce základní třídy ani nemůže být použita jako základní třída.

Další informace naleznete v tématu [abstraktní](../../extensions/abstract-cpp-component-extensions.md), [zapečetěné](../../extensions/sealed-cpp-component-extensions.md)a [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md).

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
