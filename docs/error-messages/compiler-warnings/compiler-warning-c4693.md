---
title: Upozornění kompilátoru C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 71c3db18b400ce94bff3c643d6728a6613061039
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165129"
---
# <a name="compiler-warning-c4693"></a>Upozornění kompilátoru C4693

> ' class ': zapečetěná abstraktní třída nemůže mít žádné členy instance ' test '

Pokud je typ označen jako [zapečetěný](../../extensions/sealed-cpp-component-extensions.md) a [abstraktní](../../extensions/abstract-cpp-component-extensions.md), může mít pouze statické členy.

Toto upozornění je automaticky povýšeno na chybu. Pokud chcete toto chování změnit, použijte [#pragma upozornění](../../preprocessor/warning.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```
