---
title: Chyba kompilátoru C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 094a794627b886abc7db5ba4d74c6fe97ff82461
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649734"
---
# <a name="compiler-error-c2086"></a>Chyba kompilátoru C2086

'identifier': předefinování

Identifikátor je definován více než jednou a následnou deklarací se liší od předchozího.

C2086 může být také výsledkem přírůstková sestavení pro odkazované sestavení C#. Znovu sestavte sestavení C# pro vyřešení této chyby.

Následující ukázka generuje C2086:

```
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```