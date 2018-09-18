---
title: Chyba kompilátoru C3923 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3923
dev_langs:
- C++
helpviewer_keywords:
- C3923
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b00edbb824e7815e93b961b792513a88cf96f4be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031337"
---
# <a name="compiler-error-c3923"></a>Chyba kompilátoru C3923

'member': lokální třídy, struktury nebo sjednocení definic nejsou povolené v členské funkci WinRT nebo spravované třídy

## <a name="example"></a>Příklad

Následující ukázka generuje C3923.

```
// C3923.cpp
// compile with: /clr /c
ref struct x {
   void Test() {
      struct a {};   // C3923
      class b {};   // C3923
      union c {};   // C3923
   }
};
```