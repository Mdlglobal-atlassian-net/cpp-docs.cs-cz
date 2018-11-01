---
title: Kompilátor upozornění (úroveň 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: bcadf31eda079ebb8ea7a496efe4c945e16b1ab7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622841"
---
# <a name="compiler-warning-level-1-c4532"></a>Kompilátor upozornění (úroveň 1) C4532

'příkaz continue': skok z bloku __finally/finally má během zpracování ukončení nedefinované chování

Kompilátor zjistil jednu z následujících klíčových slov:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

způsobí přechod z [__finally](../../cpp/try-finally-statement.md) nebo [nakonec](../../dotnet/finally.md) bloku během abnormální ukončení.

Pokud dojde k výjimce, a přestože je právě zachytila zásobníku při provádění obslužné rutiny ukončení ( `__finally` nebo finally blokuje), a váš kód přejde z celkového počtu `__finally` blokovat před `__finally` konce bloku, chování není definováno. Ovládací prvek nesmí vracet odvíjení kódu, proto nemusí být výjimka zpracována správně.

Pokud musíte přejít z celkového počtu **__finally** blokovat, proveďte nejprve kontrolu abnormální ukončení.

Následující ukázka generuje C4532; jednoduše Odkomentujte příkazů skoku k vyřešení upozornění.

```
// C4532.cpp
// compile with: /W1
// C4532 expected
int main() {
   int i;
   for (i = 0; i < 10; i++) {
      __try {
      } __finally {
         // Delete the following line to resolve.
         continue;
      }

      __try {
      } __finally {
         // Delete the following line to resolve.
         break;
      }
   }
}
```