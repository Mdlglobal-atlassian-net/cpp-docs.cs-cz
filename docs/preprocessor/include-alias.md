---
title: include_alias | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.include_alias
- include_alias_CPP
dev_langs:
- C++
helpviewer_keywords:
- pragmas, include_alias
- include_alias pragma
ms.assetid: 3256d589-12b3-4af0-a586-199e96eabacc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c9844c610a1b5bffab8f5fba67daff90a52412e4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065171"
---
# <a name="includealias"></a>include_alias

Určuje, že *short_filename* má být použit jako alias pro *long_filename*.

## <a name="syntax"></a>Syntaxe

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>include_alias – Direktiva pragma ("*long_filename*","*short_filename*")
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>include_alias – Direktiva pragma (*long_filename*, *short_filename*)

## <a name="remarks"></a>Poznámky

Některé systémy souborů povolují delší názvy souborů hlaviček než omezení 8.3 systému souborů FAT. Kompilátor nemůže jednoduše zkrátit delší názvy na formát 8.3, protože prvních 8 znaků delšího názvu souboru hlaviček nemusí být jedinečných. Vždy, když kompilátor narazí *long_filename* řetězec, nahradí *short_filename*a hledá soubor hlaviček *short_filename* místo. Tato direktiva pragma se musí vyskytovat před odpovídajícími direktivami `#include`. Příklad:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Hledaný alias se musí se specifikací přesně shodovat ve velikosti písmen, jejich pořadí i použití dvojitých uvozovek či ostrých závorek. **Include_alias** – Direktiva pragma provede jednoduchým řetězcem porovnávání názvů souborů; je provést žádné další ověření názvu souboru. Jsou-li například dány následující direktivy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

není zavedení aliasů (nahrazení) provedeno, protože řetězce souborů hlaviček nejsou přesně shodné. Také názvy souborů hlaviček použité jako argumenty, které mají `/Yu` a `/Yc` – možnosti kompilátoru, nebo `hdrstop` – Direktiva pragma, nejsou nahrazeny. Obsahuje-li zdrojový kód například následující direktivu,

```cpp
#include <AppleSystemHeaderStop.h>
```

měla by odpovídající možnost kompilátoru být

> /YcAppleSystemHeaderStop.h

Můžete použít **include_alias** – Direktiva pragma mapovat libovolný název souboru hlaviček na jiný. Příklad:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nezaměňujte názvy souborů uzavřené v uvozovkách s názvy souborů uzavřenými v ostrých závorkách. Například dány předchozí dvě `#pragma include_alias` direktivy, kompilátor neprovede žádné nahrazení v následujících `#include` direktivy:

```cpp
#include <api.h>
#include "stdio.h"
```

Následující direktiva dále způsobí chybu:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Všimněte si, že název souboru uvedený v chybových zprávách nebo jako hodnotu z předdefinovaných `__FILE__` název souboru je makro, po provedení nahrazení. Například po následujících direktivách zobrazit výstup:

```cpp
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )
#include "VeryLongFileName.H"
```

Chyba v VERYLONGFILENAME. H, vytvoří se následující chybová zpráva:

```Output
myfile.h(15) : error C2059 : syntax error
```

Povšimněte si také, že není podporována přenositelnost. Jsou-li dány následující direktivy,

```cpp
#pragma include_alias( "one.h", "two.h" )
#pragma include_alias( "two.h", "three.h" )
#include "one.h"
```

kompilátor hledá namísto souboru THREE.H soubor TWO.H.

## <a name="see-also"></a>Viz také

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)