---
title: Chyba kompilátoru C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 87b5afe2133bb737a8f9c855b0652c2f50ca27ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740517"
---
# <a name="compiler-error-c2601"></a>Chyba kompilátoru C2601

' function ': definice lokální funkce jsou neplatné

Kód se pokusí definovat funkci v rámci funkce.

Nebo může být ve zdrojovém kódu znak extra složené závorky před umístěním chyby C2601.

Následující ukázka generuje C2601:

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
