---
title: Upozornění kompilátoru (úroveň 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 268a26f5de1bb7f757a8e7cba6d3f5e6ddff882e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052481"
---
# <a name="compiler-warning-level-1-c4715"></a>Upozornění kompilátoru (úroveň 1) C4715

' function ': ne všechny cesty k ovládacím prvkům vrací hodnotu

Zadaná funkce nemůže vracet hodnotu.

## <a name="example"></a>Příklad

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Chcete-li zabránit tomuto upozornění, upravte kód tak, aby všechny cesty přiřadily vrácenou hodnotu funkci:

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Je možné, že váš kód může obsahovat volání funkce, která se nikdy nevrátí, jako v následujícím příkladu:

```cpp
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

Tento kód také vygeneruje upozornění, protože kompilátor neví, že `fatal` nikdy nevrátí. Chcete-li zabránit tomu, aby tento kód generoval chybovou zprávu, deklarujte `fatal` pomocí [__declspec (vrácení zpět)](../../cpp/noreturn.md).