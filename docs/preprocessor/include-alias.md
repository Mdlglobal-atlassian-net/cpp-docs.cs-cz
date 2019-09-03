---
title: include_alias – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
ms.openlocfilehash: aa3714186e8f95d4044ba5a3b2bc2d5fcfb1fc9c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218901"
---
# <a name="include_alias-pragma"></a>include_alias – direktiva pragma

Určuje, že když se v `#include` direktivě alias_filename najde, kompilátor nahradí *actual_filename* na svém místě.

## <a name="syntax"></a>Syntaxe

<!-- localization note - it's important to have the italic and bold characters immediately adjacent here. -->
> **#pragma include_alias (** "*alias_filename*" **;** "*actual_filename*" **)** \
> **#pragma include_alias (** \< *alias_filename*>  **,** *actual_filename*) \<> 

## <a name="remarks"></a>Poznámky

Direktiva pragma **include_alias** umožňuje nahradit soubory, které mají různé názvy nebo cesty pro názvy souborů, které jsou součástí zdrojových souborů. Některé systémy souborů například umožňují delší názvy souborů hlaviček, než je limit systému souborů FAT 8,3. Kompilátor nemůže pouze zkrátit delší názvy na 8,3, protože prvních osm znaků delších názvů souborů hlaviček nemusí být jedinečný. Pokaždé, když kompilátor uvidí *alias_filename* řetězec v `#include` direktivě, nahradí místo toho název *actual_filename* . Pak načte hlavičkový soubor *actual_filename* . Tato direktiva pragma se musí vyskytovat před odpovídajícími direktivami `#include`. Příklad:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Hledaný alias musí přesně odpovídat specifikaci. Velikost písmen, pravopis a použití dvojitých uvozovek a lomených závorek musí odpovídat všem. Direktiva pragma **include_alias** provádí jednoduché porovnání řetězců v názvech souborů. Neprovádí se žádné další ověření názvu souboru. Jsou-li například dány následující direktivy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

nahrazení aliasů se neprovádí, protože řetězce hlavičkového souboru se přesně neshodují. Také názvy souborů hlaviček používané jako argumenty pro `/Yu` možnosti `hdrstop` kompilátoru a a `/Yc` direktivu pragma nejsou nahrazeny. Obsahuje-li zdrojový kód například následující direktivu,

```cpp
#include <AppleSystemHeaderStop.h>
```

měla by odpovídající možnost kompilátoru být

> **/YcAppleSystemHeaderStop.h**

Pomocí direktivy pragma **include_alias** můžete mapovat libovolný název souboru hlaviček na jiný. Příklad:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nekombinujte názvy souborů uzavřené do dvojitých uvozovek s názvy souborů, které jsou uzavřeny v lomených závorkách. Například s ohledem na výše uvedené `#pragma include_alias` direktivy kompilátor neposkytuje žádné náhrady u následujících `#include` direktiv:

```cpp
#include <api.h>
#include "stdio.h"
```

Následující direktiva dále způsobí chybu:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Název souboru, který se nahlásil v chybových zprávách nebo jako hodnota `__FILE__` předdefinovaného makra, je název souboru po provedení substituce. Podívejte se například na výstup po následujících direktivách:

```cpp
#pragma include_alias( "VERYLONGFILENAME.H", "myfile.h" )
#include "VERYLONGFILENAME.H"
```

Chyba v *VERYLONGFILENAME. H* vytvoří následující chybovou zprávu:

```Output
myfile.h(15) : error C2059 : syntax error
```

Upozorňujeme také, že přenositelnost není podporováno. Jsou-li dány následující direktivy,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

kompilátor vyhledá soubor *2. h* spíše než *tři. h*.

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
