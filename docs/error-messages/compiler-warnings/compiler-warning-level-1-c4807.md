---
title: Upozornění kompilátoru (úroveň 1) C4807
ms.date: 11/04/2016
f1_keywords:
- C4807
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
ms.openlocfilehash: 2424d076be0914a68c3227566cb851b7ab64cc0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175035"
---
# <a name="compiler-warning-level-1-c4807"></a>Upozornění kompilátoru (úroveň 1) C4807

' operation ': potenciálně nebezpečné kombinace typu ' type ' a podepsaného bitového pole typu ' type '

Toto upozornění je generováno při porovnávání bitového bitu podepsaného v rámci `bool` proměnné. Vzhledem k tomu, že bitové pole s jednorázovým podpisem může obsahovat pouze hodnoty-1 nebo 0, není bezpečné ho porovnat s `bool`. Nejsou generována žádná upozornění týkající se kombinování `bool` a bitová pole bez znaménka, protože jsou identická s `bool` a mohou obsahovat pouze 0 nebo 1.

## <a name="example"></a>Příklad

Následující ukázka generuje C4807:

```cpp
// C4807.cpp
// compile with: /W1
typedef struct bitfield {
   signed mybit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bool b = true;

   // try..
   // int b = true;

   bf.mybit = -1;
   if (b == bf.mybit) {   // C4807
      b = false;
   }
}
```
