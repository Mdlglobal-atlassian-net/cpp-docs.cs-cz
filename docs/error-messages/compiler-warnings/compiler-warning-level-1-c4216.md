---
title: Upozornění (úroveň 1) C4216 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4216
dev_langs:
- C++
helpviewer_keywords:
- C4216
ms.assetid: 211079dc-59d0-42a7-801c-2ddab21d7232
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6f9e53115b7b162fa4c36ad9a3fa227de777bf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042985"
---
# <a name="compiler-warning-level-1-c4216"></a>Kompilátor upozornění (úroveň 1) C4216

používá se nestandardní rozšíření: float long

Výchozí rozšíření společnosti Microsoft (/Ze) považovat **float long** jako **double**. Kompatibilita s ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) nepodporuje. Použití **double** zachovala kompatibilita. Následující ukázka generuje C4216:

```
// C4216.cpp
// compile with: /W1
float long a;   // C4216

// use the line below to resolve the warning
// double a;

int main() {
}
```