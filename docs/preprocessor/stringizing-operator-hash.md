---
title: Operátor nastavení velikosti řetězce (#)
ms.date: 08/29/2019
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
ms.openlocfilehash: 5a1b43198e59bc1e69cdf1b56db56be75719fe46
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216550"
---
# <a name="stringizing-operator-"></a>Operátor nastavení velikosti řetězce (#)

Symbol čísla nebo operátor "převodu" ( **#** ) převede parametry makra na řetězcové literály bez rozšíření definice parametru. Používá se pouze s makry, která přijímají argumenty. Je-li operátor uveden v definici makra před formálním parametrem, je skutečný argument předaný voláním makra uzavřen do uvozovek a považován za řetězcový literál. Řetězcový literál pak nahradí všechny výskyty kombinace operátoru převodu na řetězec a formálního parametru v definici makra.

> [!NOTE]
> Rozšíření standardu ANSI jazyka C společností Microsoft (verze 6.0 a starší), ve kterém byly dříve rozvíjeny formální argumenty maker uvnitř řetězcových literálů a znakových konstant, již není podporováno. Kód, který se spoléhat na toto rozšíření, by měl být přepsán pomocí **#** operátoru převodu ().

Prázdné místo, které předchází prvnímu tokenu a následuje poslední token skutečného argumentu, je ignorováno. Všechny prázdné znaky mezi tokeny ve skutečném argumentu jsou ve výsledném řetězcovém literálu redukovány na jediný prázdný znak. Proto pokud se vyskytne komentář mezi dvěma tokeny ve skutečném argumentu, je zmenšen na jeden prázdný znak. Výsledný řetězcový literál je automaticky zřetězen se všemi sousedními řetězcovými literály, které jsou odděleny pouze prázdným znakem.

Pokud znak obsažený v argumentu obvykle vyžaduje řídící sekvenci při použití v řetězcovém literálu, například znak uvozovky (`"`) nebo zpětného lomítka (`\`), je nezbytné zpětné lomítko automaticky vloženo před znak.

Operátor Microsoft C++ převodu se chová správně, když se používá s řetězci, které obsahují řídicí sekvence. V této situaci kompilátor generuje [chybu kompilátoru C2017](../error-messages/compiler-errors-1/compiler-error-c2017.md).

## <a name="examples"></a>Příklady

Následující příklad ukazuje definici makra, která obsahuje operátor převodu a funkci main, která vyvolá makro:

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
