---
title: Chyba kompilátoru C3872
ms.date: 11/04/2016
f1_keywords:
- C3872
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
ms.openlocfilehash: 5cadb8165b5b63b2f7ac2d4cc31e2623b0f6bce9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50649891"
---
# <a name="compiler-error-c3872"></a>Chyba kompilátoru C3872

! char': Tento znak není v identifikátoru povolený.

Kompilátor C++ 11 standard C ++ následuje na znaky v identifikátoru povolený. Jenom určitých rozsahů znaků a univerzální názvy znaků jsou v identifikátoru povolený. Další omezení se použijí pro počáteční znak identifikátoru. Další informace a seznam povolených znaků a název rozsahy univerzálních znaků naleznete v tématu [identifikátory](../../cpp/identifiers-cpp.md).

Rozsah znaků v identifikátoru povolený je méně omezující při kompilaci C + +/ CLI kódu. Identifikátory v kódu zkompilovaném pomocí/CLR by měly dodržovat [Standard ECMA-335: Common Language infrastruktury (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).

Následující ukázka generuje C3872:

```
// C3872.cpp
int main() {
   int abc_\u0040;   // C3872, U+0040 is in base char set
   int abc_\u3001;   // C3872, U+3001 is not in allowed range
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range
}
```