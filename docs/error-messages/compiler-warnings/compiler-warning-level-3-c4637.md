---
title: Upozornění kompilátoru (úroveň 3) C4637
ms.date: 11/04/2016
f1_keywords:
- C4637
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
ms.openlocfilehash: 28362e186f2cb841f4abb67175984bcd8b4f0cf7
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991787"
---
# <a name="compiler-warning-level-3-c4637"></a>Upozornění kompilátoru (úroveň 3) C4637

Cíl komentáře k dokumentu XML: \<zahrnout zahozenou > značku.  reason

Syntaxe [\<include >](../../build/reference/include-visual-cpp.md) nebyla správná.

Následující ukázka generuje C4637:

```cpp
// C4637.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <include file="c:\davedata\jtest\xml_include.doc"/>
   // Try the following line instead:
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />
   void MyMethod() {
   }
};   // C4637
```
