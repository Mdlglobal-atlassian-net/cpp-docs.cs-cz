---
title: Compiler Error C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: f18819e5f078cb85121160af1d4a3fc24a365a68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62215580"
---
# <a name="compiler-error-c2601"></a>Compiler Error C2601

'function': definice lokální funkce jsou neplatné

Kód se pokusí definovat funkci v rámci funkce.

Nebo může být navíc složenou závorku ve zdrojovém kódu před umístění C2601 chyby.

Následující ukázka generuje C2601:

```
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```