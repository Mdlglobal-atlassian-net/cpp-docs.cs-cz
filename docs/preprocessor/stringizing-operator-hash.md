---
title: Operátor nastavení velikosti řetězce (#)
ms.date: 11/04/2016
f1_keywords:
- '#'
helpviewer_keywords:
- preprocessor, operators
- arguments [C++], converting to strings
- stringizing operator
- preprocessor
- string literals, converting macro parameters to
- macros [C++], converting parameters to strings
- '# preprocessor operator'
ms.assetid: 1175dd19-4538-43b3-ad97-a008ab80e7b1
ms.openlocfilehash: d90d07c8f3cce6c443be0eb994db494746c00fcc
ms.sourcegitcommit: 40ffe764244784c715b086c79626ac390b855d47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711144"
---
# <a name="stringizing-operator-"></a>Operátor nastavení velikosti řetězce (#)

Symbol čísla nebo operátor "převodu" ( **#** ) převede parametry makra na řetězcové literály bez rozšíření definice parametru. Používá se pouze spolu s makry, která přijímají argumenty. Je-li operátor uveden v definici makra před formálním parametrem, je skutečný argument předaný voláním makra uzavřen do uvozovek a považován za řetězcový literál. Řetězcový literál pak nahradí všechny výskyty kombinace operátoru převodu na řetězec a formálního parametru v definici makra.

> [!NOTE]
> Rozšíření standardu ANSI jazyka C společností Microsoft (verze 6.0 a starší), ve kterém byly dříve rozvíjeny formální argumenty maker uvnitř řetězcových literálů a znakových konstant, již není podporováno. Kód, který se spoléhat na toto rozšíření, by měl být přepsán pomocí **#** operátoru převodu ().

Prázdný znak před prvním a za posledním tokenem skutečného argumentu je ignorován. Všechny prázdné znaky mezi tokeny ve skutečném argumentu jsou ve výsledném řetězcovém literálu redukovány na jediný prázdný znak. Proto vyskytne-li se mezi dvěma tokeny ve skutečném argumentu komentář, je redukován na jediný prázdný znak. K výslednému řetězcovému literálu jsou automaticky připojeny všechny sousedící řetězcové literály, od nichž je výsledný literál oddělen pouze prázdnými znaky.

Pokud znak obsažený v argumentu obvykle vyžaduje řídící sekvenci při použití v řetězcovém literálu (například znak uvozovky ( **"** ) nebo zpětného lomítka ( **\\** )), je nutné automaticky vložit zpětné lomítko. před znakem.

Operátor Visual C++ převodu se chová správně, když je použit s řetězci, které obsahují řídicí sekvence. V této situaci kompilátor generuje [chybu kompilátoru C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).

## <a name="examples"></a>Příklady

Následující příklad ukazuje definici makra obsahující operátor převodu na řetězec a hlavní funkci, která makro volá:

```cpp
// stringizer.cpp
#include <stdio.h>
#define stringer( x ) printf_s( #x "\n" )
int main() {
   stringer( In quotes in the printf function call );
   stringer( "In quotes when printed to the screen" );
   stringer( "This: \"  prints an escaped double quote" );
}
```

`stringer` Makra jsou rozšířena během předběžného zpracování a vytváří následující kód:

```cpp
int main() {
   printf_s( "In quotes in the printf function call" "\n" );
   printf_s( "\"In quotes when printed to the screen\"" "\n" );
   printf_s( "\"This: \\\" prints an escaped double quote\"" "\n" );
}
```

```Output
In quotes in the printf function call
"In quotes when printed to the screen"
"This: \"  prints an escaped double quote"
```

Následující příklad ukazuje, jak lze rozvinout parametr makra:

```cpp
// stringizer_2.cpp
// compile with: /E
#define F abc
#define B def
#define FB(arg) #arg
#define FB1(arg) FB(arg)
FB(F B)
FB1(F B)
```

## <a name="see-also"></a>Viz také:

[Operátory preprocesoru](../preprocessor/preprocessor-operators.md)
