---
title: Chyba kompilátoru C2197
ms.date: 11/04/2016
f1_keywords:
- C2197
helpviewer_keywords:
- C2197
ms.assetid: 6dd5a6ec-bc80-41b9-a4ac-46f80eaca42d
ms.openlocfilehash: 16bc1b17b13cb9c7507a769f644eb34faa4989de
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301844"
---
# <a name="compiler-error-c2197"></a>Chyba kompilátoru C2197

' function ': moc velký počet argumentů pro volání

Kompilátor zjistil příliš mnoho parametrů pro volání funkce nebo nesprávnou deklaraci funkce.

Následující ukázka generuje C2197:

```c
// C2197.c
// compile with: /Za /c
void func( int );
int main() {
   func( 1, 2 );   // C2197 two actual parameters
   func( 2 );   // OK
}
```
