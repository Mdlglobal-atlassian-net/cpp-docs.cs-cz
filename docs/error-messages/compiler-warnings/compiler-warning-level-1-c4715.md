---
title: Upozornění (úroveň 1) C4715 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4715
dev_langs:
- C++
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7b3de829992bfa650280768a2fcd761feaeaece0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061367"
---
# <a name="compiler-warning-level-1-c4715"></a>Kompilátor upozornění (úroveň 1) C4715

'function': Ne všechny cesty ovládacích prvků vracet hodnotu

Zadaná funkce může potenciálně nesmí vracet hodnotu.

## <a name="example"></a>Příklad

```
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Aby se zabránilo toto upozornění, upravte kód tak, aby všechny cesty přiřadit návratovou hodnotu funkce:

```
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Je možné, že váš kód může obsahovat volání funkce, která se nikdy vrátí, jako v následujícím příkladu:

```
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

Tento kód také vygeneruje upozornění, protože kompilátor, který nezná `fatal` nikdy nevrátí. Chcete-li zabránit tento kód vygeneruje chybovou zprávu, deklarujte `fatal` pomocí [__declspec(noreturn)](../../cpp/noreturn.md).