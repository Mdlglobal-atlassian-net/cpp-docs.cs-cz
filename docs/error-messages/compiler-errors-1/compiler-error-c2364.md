---
title: Chyba kompilátoru C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: 051468ea861190dd3f6a28dc272f1bab155145af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558896"
---
# <a name="compiler-error-c2364"></a>Chyba kompilátoru C2364

'type': Neplatný typ pro vlastní atribut

Pojmenované argumenty pro vlastní atributy jsou omezené na konstanty z doby kompilace. Například celočíselných typů (int, char, atd.), System::Type ^ a System::Object ^.

## <a name="example"></a>Příklad

Následující ukázka generuje C2364.

```
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```