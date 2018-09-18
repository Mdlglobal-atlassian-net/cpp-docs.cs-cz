---
title: Chyba kompilátoru C3195 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3195
dev_langs:
- C++
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c299704b595ca6e6f6b81fb56ffad5534f81e6b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040593"
---
# <a name="compiler-error-c3195"></a>Chyba kompilátoru C3195

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