---
title: Chyba kompilátoru C2530 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2530
dev_langs:
- C++
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f41f9ec64e2074ed5e0cd2654f2b6bfec886bc07
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103182"
---
# <a name="compiler-error-c2530"></a>Chyba kompilátoru C2530

'identifier': odkazy musí být inicializován.

Odkaz musí inicializovat při jeho deklaraci byl, pokud je už deklarovaná:

- S klíčovým slovem [extern](../../cpp/using-extern-to-specify-linkage.md).

- Jako člen třídy, struktury nebo sjednocení (a je inicializována v konstruktoru).

- Jako parametr v definici nebo deklaraci funkce.

- Jako návratový typ funkce.

Následující ukázka generuje C2530:

```
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```