---
title: Operátor vkládající token (##)
ms.date: 08/29/2019
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: 4bf1b8c8f56ab9375503c9e8fb6a906706fc70bb
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218114"
---
# <a name="token-pasting-operator-"></a>Operátor vkládající token (##)

Operátor dvojitého znaménka nebo operátor *vložení tokenu* ( **##** ), který se někdy označuje jako operátor *sloučení* nebo *kombinování* , se používá v makrech podobných objektech a funkcích. Umožňuje připojit samostatné tokeny do jediného tokenu, a proto nemůže být prvním nebo posledním tokenem v definici makra.

Pokud je formální parametr v definici makra předcházen nebo následován operátorem vložení tokenu, je formální parametr okamžitě nahrazen nerozbaleným vlastním argumentem. Rozšíření makra není na argumentu provedeno před nahrazením.

Následně se odeberou všechny výskyty operátoru vložení tokenu v *řetězci tokenu* a pak se zřetězí tokeny předcházející a následující. Výsledný token musí být platný token. V takovém případě je tento token prověřen pro možná nahrazení, pokud představuje název makra. Identifikátor představuje název, kterým bude tento zřetězený token v programu před nahrazením znám. Každý token představuje token definovaný jinde, buď v programu, nebo na příkazovém řádku kompilátoru. Mezera před nebo za tímto operátorem je nepovinná.

Tento příklad ukazuje použití operátorů převodu na řetězec a vložení tokenu v určeném výstupu programu:

```cpp
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;
```

Je-li makro voláno s číselným argumentem jako

```cpp
paster( 9 );
```

vrátí makro výraz

```cpp
printf_s( "token" "9" " = %d", token9 );
```

, který se stane

```cpp
printf_s( "token9 = %d", token9 );
```

## <a name="example"></a>Příklad

```cpp
// preprocessor_token_pasting.cpp
#include <stdio.h>
#define paster( n ) printf_s( "token" #n " = %d", token##n )
int token9 = 9;

int main()
{
   paster(9);
}
```

```Output
token9 = 9
```

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)
