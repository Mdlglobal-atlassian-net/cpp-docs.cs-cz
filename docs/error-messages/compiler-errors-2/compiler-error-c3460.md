---
title: Chyba kompilátoru C3460
ms.date: 11/04/2016
f1_keywords:
- C3460
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
ms.openlocfilehash: 9ffbc5102855574aba668a2c501cd08dbaebe5b8
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777936"
---
# <a name="compiler-error-c3460"></a>Chyba kompilátoru C3460

'type': předávat dál se dají jenom typ definovaný uživatelem

Další informace najdete v tématu [předávání typu (C++vyhodnocovací)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Příklad

Následující příklad vytvoří komponentu.

```
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>Příklad

Následující ukázka generuje C3460.

```
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```