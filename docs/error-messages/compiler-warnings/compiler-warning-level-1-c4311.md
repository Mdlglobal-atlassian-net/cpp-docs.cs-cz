---
title: Upozornění (úroveň 1) C4311 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e01aef8ffe6314452ad4644f2192583c89a42ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114420"
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