---
title: C4694 upozornění kompilátoru | Microsoft Docs
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4694
dev_langs:
- C++
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33852b76f23e007625f86969119a22ee81305187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4694"></a>C4694 upozornění kompilátoru

> '*třída*': zapečetěné abstraktní třídy nemají základní třídy*base_class*.

Třídu abstraktní a uzavřené nemůže Zdědit z typu odkazu; uzavřený a abstraktní třídu můžete implementovat funkce základní třídy ani mohl použít jako základní třída.

Další informace najdete v tématu [abstraktní](../../windows/abstract-cpp-component-extensions.md), [zapečetěné](../../windows/sealed-cpp-component-extensions.md), a [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md).

Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```