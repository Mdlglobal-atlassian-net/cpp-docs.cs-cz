---
title: "C4693 upozornění kompilátoru | Microsoft Docs"
ms.date: 10/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4693
dev_langs: C++
helpviewer_keywords: C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3e5d7b93295505d989e651500dda0664c1a13a36
ms.sourcegitcommit: 69632887f7a85f4841c49b4c1353d3144927a52c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2017
---
# <a name="compiler-warning-c4693"></a>C4693 upozornění kompilátoru

> 'class': zapečetěné abstraktní třídy nemůže mít u členů instancí "Test"

Pokud je označena jako typ [zapečetěné](../../windows/sealed-cpp-component-extensions.md) a [abstraktní](../../windows/abstract-cpp-component-extensions.md), může mít pouze statické členy.

Toto upozornění je automaticky povýšen na chybu. Pokud chcete-li toto chování změnit, použijte [#pragma – upozornění](../../preprocessor/warning.md).

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