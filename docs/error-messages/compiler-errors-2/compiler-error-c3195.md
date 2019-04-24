---
title: Compiler Error C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: 4a54a9c629a1abaa4f1c5d15d06448e82cf25561
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62329098"
---
# <a name="compiler-error-c3195"></a>Compiler Error C3195

'operator': je vyhrazené a nejde použít jako člen ref class nebo hodnotového typu. Operátory CLR nebo WinRT musí být definovány pomocí klíčového slova operator.

Kompilátor zjistil definici operátoru pomocí spravovaných rozšíření syntaxe jazyka C++. Pro operátory, je nutné použít syntaxi jazyka C++.

Následující ukázka generuje C3195 a ukazuje, jak ho opravit:

```
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```