---
title: Upozornění kompilátoru (úroveň 1) C4312
ms.date: 11/04/2016
f1_keywords:
- C4312
helpviewer_keywords:
- C4312
ms.assetid: 541906ed-4f62-4bcb-947f-cf9ae7411bcb
ms.openlocfilehash: 83f8aa5d03bddde58f9edd4ffc9f19073045da30
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966094"
---
# <a name="compiler-warning-level-1-c4312"></a>Upozornění kompilátoru (úroveň 1) C4312

'operation': převod z 'type1' na 'type2' větší velikosti

Toto upozornění detekuje pokus o přiřazení 32 hodnoty k typu ukazatele na 64, například přetypování 32-bit `int` nebo `long` 64 na 16bitový ukazatel.

To může být nebezpečný převod i pro hodnoty ukazatele, které se vejdou v 32 bitech, když dojde k rozšíření podpisu. Pokud je záporné celé číslo 32, které je přiřazeno k typu ukazatele 64, přípona znaménka způsobí, že hodnota ukazatele odkazuje na adresu paměti odlišnou od hodnoty celého čísla.

Toto upozornění je vystaveno pouze pro 64 cíle kompilace. Další informace najdete v tématu [pravidla pro použití ukazatelů](/windows/win32/WinProg64/rules-for-using-pointers).

Následující příklad kódu generuje C4312 při kompilování pro 64 cíle:

```cpp
// C4312.cpp
// compile by using: cl /W1 /LD C4312.cpp
void* f(int i) {
   return (void*)i;   // C4312 for 64-bit targets
}

void* f2(__int64 i) {
   return (void*)i;   // OK
}
```