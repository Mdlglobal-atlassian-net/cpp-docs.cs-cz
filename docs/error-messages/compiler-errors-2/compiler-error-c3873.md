---
title: Chyba kompilátoru C3873
ms.date: 11/04/2016
f1_keywords:
- C3873
helpviewer_keywords:
- C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
ms.openlocfilehash: ca70af12ef3223c8c5950f0fa98b1c63a2dd3a4c
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450818"
---
# <a name="compiler-error-c3873"></a>Chyba kompilátoru C3873

! char': Tento znak není povolený jako první znak identifikátoru

Kompilátor C++ 11 standard C ++ následuje na znaky v identifikátoru povolený. Jenom určitých rozsahů znaků a univerzální názvy znaků jsou v identifikátoru povolený. Další omezení se použijí pro počáteční znak identifikátoru. Další informace a seznam povolených znaků a název rozsahy univerzálních znaků naleznete v tématu [identifikátory](../../cpp/identifiers-cpp.md).

Rozsah znaků v identifikátoru povolený je méně omezující při kompilaci C++vyhodnocovací kódu. Identifikátory v kódu zkompilovaném pomocí/CLR by měly dodržovat [Standard ECMA-335: Common Language Infrastructure (CLI)](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Následující ukázka generuje C3873:

```
// C3873.cpp
int main() {
   int \u036F_abc;   // C3873, not in allowed range for initial character
   int abc_\u036F;   // OK, in allowed range for non-initial character
}
```