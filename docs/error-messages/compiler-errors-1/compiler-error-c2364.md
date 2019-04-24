---
title: Chyba kompilátoru C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: 051468ea861190dd3f6a28dc272f1bab155145af
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230396"
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