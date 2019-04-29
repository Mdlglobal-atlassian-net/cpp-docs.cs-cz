---
title: Chyba kompilátoru C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 2c8164cad25d68ee61ff9fed7170482d5dfc9505
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386990"
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