---
title: Chyba kompilátoru C2431 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2431
dev_langs:
- C++
helpviewer_keywords:
- C2431
ms.assetid: 88a5b648-c89f-47d1-a20e-63231ab4f0f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 944bead5439abf686fd18e436664e3c1cf7bccb5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049953"
---
# <a name="compiler-error-c2431"></a>Chyba kompilátoru C2431

Neplatný registr indexu 'identifier'

ESP registrace je škálovat nebo používá jako index a základní registrace. SOUROZENCŮ kódování x86 procesoru buď není povolena.

Následující ukázka generuje C2431:

```
// C2431.cpp
// processor: x86
int main() {
   _asm mov ax, [ESI + 2*ESP]   // C2431
   _asm mov ax, [esp + esp]   // C2431
}
```