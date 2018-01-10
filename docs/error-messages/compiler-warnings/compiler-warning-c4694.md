---
title: "C4694 upozornění kompilátoru | Microsoft Docs"
ms.date: 10/25/2017
ms.technology: cpp-tools
ms.topic: article
f1_keywords: C4694
dev_langs: C++
helpviewer_keywords: C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3f635aad0039812b50bd48a36f307ab5f60cba10
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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