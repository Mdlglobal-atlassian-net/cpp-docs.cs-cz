---
title: Upozornění kompilátoru (úroveň 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 7dba86d591f18fd7c9c562078204916000d47384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175321"
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
