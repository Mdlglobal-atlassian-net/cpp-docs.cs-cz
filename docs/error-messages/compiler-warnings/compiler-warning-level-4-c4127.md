---
title: C4127 kompilátoru (úroveň 4) upozornění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/13/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4127
dev_langs:
- C++
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 80f831d527e918fce0551f6a1336fd2fe994917d
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161278"
---
# <a name="compiler-warning-level-4-c4127"></a>Kompilátor C4127 upozornění (úroveň 4)

> podmíněný výraz je konstantní.

## <a name="remarks"></a>Poznámky

Řídicí výraz **Pokud** příkazu nebo **při** smyčky je vyhodnocen jako konstanta. Z důvodu jejich společné idiomatickou využití, od Visual Studio 2015 update 3, jako je například 1 triviální konstanty nebo **true** nespouštějí upozornění, pokud nejsou výsledek operace ve výrazu.

Pokud kontrolní výraz **při** smyčky je konstanta, vzhledem k tomu, opakování ve smyčce ukončeno uprostřed, zvažte nahrazení **při** smyčky s **pro** smyčky. Můžete vynechat inicializaci, ukončení testu a opakovat přírůstek **pro** smyčky, což způsobí, že smyčka bude neomezený, stejně jako `while(1)`, a můžete ukončení smyčky z textu **pro** příkaz.

## <a name="example"></a>Příklad

Následující příklad ukazuje dva způsoby C4127 se vygeneruje a ukazuje způsob použití smyčky for, aby se zabránilo upozornění:

```cpp
// C4127.cpp
// compile with: /W4
#include <stdio.h>
int main() {
   if (true) {}           // OK in VS2015 update 3 and later
   if (1 == 1) {}         // C4127
   while (42) { break; }  // C4127

   // OK
   for ( ; ; ) {
      printf("test\n");
      break;
   }
}
```