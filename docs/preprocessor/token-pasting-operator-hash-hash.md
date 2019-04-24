---
title: Operátor vložení tokenu (##)
ms.date: 11/04/2016
f1_keywords:
- '##'
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
ms.openlocfilehash: dab4da5fd65fc280d2061256a580a015917d24b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179591"
---
# <a name="token-pasting-operator-"></a>Operátor vložení tokenu (##)

Operátor double znak čísla neboli "vložení tokenu" (**##**), který se někdy nazývá operátor "slučování", se používá v makrech objektu a podobné funkce. Umožňuje sloučit samostatné tokeny do jediného tokenu, a proto nemůže být prvním nebo posledním tokenem v definici makra.

Pokud je formální parametr v definici makra předcházen nebo následován operátorem vložení tokenu, je formální parametr okamžitě nahrazen nerozbaleným vlastním argumentem. Rozšíření makra není na argumentu provedeno před nahrazením.

Poté je každý výskyt operátoru vložení tokenu v *řetězci tokenu* je odebrán a tokeny předcházejí a následují, jsou zřetězeny. Výsledný token musí být platný token. V takovém případě je tento token prověřen pro možná nahrazení, pokud představuje název makra. Identifikátor představuje název, kterým bude tento zřetězený token v programu před nahrazením znám. Každý token představuje token definovaný jinde, buď v programu, nebo na příkazovém řádku kompilátoru. Mezera před nebo za tímto operátorem je nepovinná.

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