---
title: Upozornění kompilátoru (úroveň 1) C4532
ms.date: 11/04/2016
f1_keywords:
- C4532
helpviewer_keywords:
- C4532
ms.assetid: 4e2a286a-d233-4106-9f65-29be1a94ca02
ms.openlocfilehash: b47eb192bc01e6fe2c6c9423ed2c672f16c6818f
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966254"
---
# <a name="compiler-warning-level-1-c4532"></a>Upozornění kompilátoru (úroveň 1) C4532

Continue: skok mimo __finally blok/finally má během zpracování ukončení nedefinované chování.

Kompilátor narazil na jedno z následujících klíčových slov:

- [continue](../../cpp/continue-statement-cpp.md)

- [break](../../cpp/break-statement-cpp.md)

- [goto](../../cpp/goto-statement-cpp.md)

způsobuje skok z [__finally](../../cpp/try-finally-statement.md) nebo [finally](../../dotnet/finally.md) bloku během abnormálního ukončení.

Pokud dojde k výjimce a v průběhu provádění obslužných rutin ukončení (`__finally` nebo finally) se zásobník odpustí a váš kód přeskočí `__finally` bloku před ukončením bloku `__finally`, chování není definováno. Ovládací prvek se nemůže vrátit zpět do kódu unwind, takže výjimka nemusí být zpracována správně.

Pokud je nutné přejít z **__finally** bloku, nejprve zrušte normální ukončení.

Následující ukázka generuje C4532; Stačí jednoduše komentovat příkazy skoku a vyřešit upozornění.

```cpp
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