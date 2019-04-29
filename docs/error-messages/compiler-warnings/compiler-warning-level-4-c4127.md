---
title: Kompilátor C4127 upozornění (úroveň 4)
ms.date: 09/13/2018
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 7f1e23d15d8daa126987278611cb5a85a5a36fc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401306"
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