---
title: Upozornění kompilátoru (úroveň 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 6e44dafb6675882a1a62fba5144f85120378421d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510059"
---
# <a name="compiler-warning-level-1-c4311"></a>Upozornění kompilátoru (úroveň 1) C4311

'variable': zkrácení ukazatele z 'type' na 'type'

Toto upozornění detekuje problémy zkrácení ukazatele na 64. Například pokud je kód kompilován pro 64 bitovou architekturu, hodnota ukazatele (64 bitů) bude zkrácena, pokud je přiřazena k `int` (32 bitů). Další informace najdete v tématu [pravidla pro použití ukazatelů](/windows/win32/WinProg64/rules-for-using-pointers).

Další informace o běžných příčinách upozorňujících na C4311 najdete v tématu [běžné chyby kompilátoru](/windows/win32/WinProg64/common-compiler-errors).

Následující příklad kódu generuje C4311 při kompilování pro 64 cíl a poté ukazuje, jak je opravit:

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```