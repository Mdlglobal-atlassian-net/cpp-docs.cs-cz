---
title: Upozornění kompilátoru C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: cac5918eb4a1689fd215e07272958eeca48247ad
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779437"
---
# <a name="compiler-warning-c4693"></a>Upozornění kompilátoru C4693

> 'class': zapečetěná abstraktní třída nemůže mít žádné členy instancí "Test"

Pokud je typ označen [zapečetěné](../../extensions/sealed-cpp-component-extensions.md) a [abstraktní](../../extensions/abstract-cpp-component-extensions.md), může mít jenom statické členy.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete toto chování upravit, použijte [varování #pragma](../../preprocessor/warning.md).

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