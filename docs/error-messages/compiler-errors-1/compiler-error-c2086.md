---
title: Chyba kompilátoru C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735746"
---
# <a name="compiler-error-c2086"></a>Chyba kompilátoru C2086

' identifier ': předefinování

Identifikátor je definován více než jednou nebo následná deklarace se liší od předchozí deklarace.

C2086 může být také výsledkem přírůstkového sestavování pro odkazované C# sestavení. Pro vyřešení této C# chyby znovu sestavte sestavení.

Následující ukázka generuje C2086:

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
