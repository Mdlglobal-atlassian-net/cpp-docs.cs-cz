---
title: Upozornění (úroveň 4) C4706 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4706
dev_langs:
- C++
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 843edeaf490f27475003e9303f7929b818e2b104
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036953"
---
# <a name="compiler-warning-level-4-c4706"></a>Kompilátor upozornění (úroveň 4) C4706

přiřazení podmíněného výrazu

Testovací hodnotu v podmíněném výrazu byl výsledek přiřazení.

Přiřazení má hodnotu (hodnoty na levé straně přiřazení), která je možné právně v jiný výraz, včetně výrazu testu.

Následující ukázka generuje C4706:

```
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

Upozornění dojde i v případě, že Dvojité závorky kolem testovací podmínku:

```
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

Pokud je vaším záměrem je testovací relaci a Nedělejte přiřazení, použijte `==` operátor. Například následující řádek testů Určuje, zda a b jsou stejné:

```
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

Pokud máte v úmyslu provést test hodnota výsledek přiřazení, testování pro zajištění, že přiřazení je nenulová nebo not null. Následující kód například nevygeneruje toto upozornění:

```
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```