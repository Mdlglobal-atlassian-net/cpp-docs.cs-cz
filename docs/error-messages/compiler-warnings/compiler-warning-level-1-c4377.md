---
title: Upozornění (úroveň 1) C4377 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4377
dev_langs:
- C++
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 613ebe183b61c6b9894ed3b726f90061e2b24ef6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047171"
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