---
title: Upozornění kompilátoru (úroveň 4) C4127
ms.date: 10/16/2019
f1_keywords:
- C4127
helpviewer_keywords:
- C4127
ms.assetid: f59ded9e-5227-45bd-ac43-2aa861581363
ms.openlocfilehash: 52a966bb321226058afbf4667a4192e4e814f0a1
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075858"
---
# <a name="compiler-warning-level-4-c4127"></a>Upozornění kompilátoru (úroveň 4) C4127

> podmíněný výraz je konstanta

## <a name="remarks"></a>Poznámky

Řídicí výraz příkazu **if** nebo **while** je vyhodnocen jako konstanta. Vzhledem k tomu, že se jedná o běžné použití idiomatickou, počínaje verzí Visual Studio 2015 Update 3, triviální konstanty jako 1 nebo **true** neaktivují upozornění, pokud se nejedná o výsledek operace ve výrazu.

Pokud řídicí výraz smyčky **while** je konstanta, protože smyčka končí uprostřed, zvažte nahrazení smyčky **while** smyčkou **for** . Můžete vynechat stav inicializace, ukončení testu a smyčka smyčky **for** , což způsobí, že smyčka bude nekonečná, stejně jako `while(1)`, a můžete ukončit smyčku z těla příkazu **for** .

## <a name="example"></a>Příklad

Následující příklad ukazuje dva způsoby, jak se vygeneruje C4127, a ukazuje, jak použít smyčku for, abyste se vyhnuli upozornění:

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

Toto upozornění je také možné vygenerovat při použití konstanty v době kompilace v podmíněném výrazu:

```cpp
#include <string>

using namespace std;

template<size_t S, class T>
void MyFunc()
{
   if (sizeof(T) >= S) // C4127. "Consider using 'if constexpr' statement instead"
   {
   }
}

class Foo
{
   int i;
   string s;
};

int main()
{
   Foo f;
   MyFunc<4, Foo>();
}
```