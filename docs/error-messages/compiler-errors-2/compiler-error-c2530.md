---
title: Chyba kompilátoru C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737124"
---
# <a name="compiler-error-c2530"></a>Chyba kompilátoru C2530

' identifier ': odkazy musí být inicializovány

Je nutné inicializovat odkaz při jeho deklaraci, pokud není deklarována již:

- Pomocí klíčového slova [extern](../../cpp/using-extern-to-specify-linkage.md).

- Jako člen třídy, struktury nebo sjednocení (a je inicializován v konstruktoru).

- Jako parametr v deklaraci nebo definici funkce.

- Jako návratový typ funkce.

Následující ukázka generuje C2530:

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
