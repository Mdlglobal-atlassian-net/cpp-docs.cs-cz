---
title: Kompilátor upozornění (úroveň 1) C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: d8c89967e0dc900e098ca03d22932451f26a6a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531017"
---
# <a name="compiler-warning-level-1-c4377"></a>Kompilátor upozornění (úroveň 1) C4377

nativní typy jsou privátní ve výchozím nastavení; -d1PrivateNativeTypes je zastaralá.

V předchozích verzích byly nativní typy v sestavení veřejné ve výchozím nastavení a – možnost kompilátoru interní, nedokumentované (**/d1PrivateNativeTypes**) byla použita k je soukromá.

Všechny typy, nativní a CLR, jsou teď ve výchozím nastavení v sestavení, privátní, **/d1PrivateNativeTypes** už nepotřebujete.

## <a name="example"></a>Příklad

Následující ukázka generuje C4377.

```
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```