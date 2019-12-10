---
title: Upozornění kompilátoru (úroveň 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: 2ff8794dcf29539b492f53bfdf6f0810988c0f72
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989902"
---
# <a name="compiler-warning-level-4-c4706"></a>Upozornění kompilátoru (úroveň 4) C4706

přiřazení v rámci podmíněného výrazu

Hodnota testu v podmíněném výrazu byla výsledkem přiřazení.

Přiřazení má hodnotu (hodnotu na levé straně přiřazení), kterou lze použít právně v jiném výrazu, včetně testovacího výrazu.

Následující ukázka generuje C4706:

```cpp
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

Upozornění bude provedeno i v případě, že podržíte závorky kolem zkušební podmínky:

```cpp
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

Pokud máte v úmyslu testovat relaci, ale nechcete provést přiřazení, použijte operátor `==`. Například následující řádek testuje, zda jsou a a b stejné:

```cpp
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

Pokud máte v úmyslu převést hodnotu testu na výsledek přiřazení, otestujte test, aby bylo zajištěno, že přiřazení je nenulové nebo není null. Například následující kód nebude generovat toto upozornění:

```cpp
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
