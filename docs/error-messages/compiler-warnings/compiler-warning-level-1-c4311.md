---
title: Kompilátor upozornění (úroveň 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 5f9b8ce710879913fdad1be5c0f22f8e3f4ed9d7
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51518161"
---
# <a name="compiler-warning-level-1-c4311"></a>Kompilátor upozornění (úroveň 1) C4311

'variable': zkrácení ukazatele z 'type' na 'type'

Toto upozornění zjistí problémy zkrácení 64bitového ukazatele. Například pokud kód je zkompilován pro 64bitová architektura, hodnotou ukazatele (64bitová verze) se zkrátí Pokud je přiřazen `int` (32bitová verze). Další informace najdete v tématu [pravidla pro používání ukazatele](/windows/desktop/WinProg64/rules-for-using-pointers).

Další informace o běžných příčin upozornění C4311 najdete v tématu [běžné chyby kompilátoru](/windows/desktop/WinProg64/common-compiler-errors).

Následující příklad kódu generuje C4311 při kompilaci pro 64bitové cílové a uvidíte, jak ho opravit:

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```