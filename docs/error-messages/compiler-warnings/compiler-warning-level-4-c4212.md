---
title: Upozornění (úroveň 4) C4212 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4212
dev_langs:
- C++
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 107581742f1a60cfc015a9a1b8ccea8b2f89c7a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074757"
---
# <a name="compiler-warning-level-4-c4212"></a>Kompilátor upozornění (úroveň 4) C4212

používá se nestandardní rozšíření: deklarace funkce se používají tři tečky

Prototyp funkce má proměnný počet argumentů. Definice funkce je nepodporuje.

Následující ukázka generuje C4212:

```
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```