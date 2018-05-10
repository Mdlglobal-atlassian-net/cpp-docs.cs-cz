---
title: include_alias – | Microsoft Docs
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
ms.openlocfilehash: 84e09b51d6f234bdc17353c358e378f18e153567
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="includealias"></a>include_alias

Určuje, že *short_filename* se má použít jako alias pro *long_filename*.

## <a name="syntax"></a>Syntaxe

> #<a name="pragma-includealiaslongfilename-shortfilename"></a>include_alias – Direktiva pragma ("*long_filename*","*short_filename*")  
> #<a name="pragma-includealiaslongfilename-shortfilename"></a>include_alias – Direktiva pragma (*long_filename*, *short_filename*)

## <a name="remarks"></a>Poznámky

Některé systémy souborů povolují delší názvy souborů hlaviček než omezení 8.3 systému souborů FAT. Kompilátor nemůže jednoduše zkrátit delší názvy na formát 8.3, protože prvních 8 znaků delšího názvu souboru hlaviček nemusí být jedinečných. Vždy, když kompilátor narazí *long_filename* řetězci nahradí *short_filename*a hledá soubor hlaviček *short_filename* místo. Tato direktiva pragma se musí vyskytovat před odpovídajícími direktivami `#include`. Příklad:

```cpp
// First eight characters of these two files not unique.
#pragma include_alias( "AppleSystemHeaderQuickdraw.h", "quickdra.h" )
#pragma include_alias( "AppleSystemHeaderFruit.h", "fruit.h" )

#pragma include_alias( "GraphicsMenu.h", "gramenu.h" )

#include "AppleSystemHeaderQuickdraw.h"
#include "AppleSystemHeaderFruit.h"
#include "GraphicsMenu.h"
```

Hledaný alias se musí se specifikací přesně shodovat ve velikosti písmen, jejich pořadí i použití dvojitých uvozovek či ostrých závorek. **Include_alias –** – Direktiva pragma provede jednoduchým řetězcem porovnávání s názvy souborů; žádné filename ověření. Jsou-li například dány následující direktivy,

```cpp
#pragma include_alias("mymath.h", "math.h")
#include "./mymath.h"
#include "sys/mymath.h"
```

není zavedení aliasů (nahrazení) provedeno, protože řetězce souborů hlaviček nejsou přesně shodné. Navíc záhlaví názvy souborů používá jako argumenty pro možnosti kompilátoru /Yu a /Yc nebo **hdrstop –** – Direktiva pragma, nejsou nahrazena. Obsahuje-li zdrojový kód například následující direktivu,
  
```cpp
#include <AppleSystemHeaderStop.h>
```

měla by odpovídající možnost kompilátoru být

> /YcAppleSystemHeaderStop.h

Můžete použít **include_alias –** – Direktiva pragma pro mapování všechny hlavičky název souboru do druhého. Příklad:

```cpp
#pragma include_alias( "api.h", "c:\version1.0\api.h" )
#pragma include_alias( <stdio.h>, <newstdio.h> )
#include "api.h"
#include <stdio.h>
```

Nezaměňujte názvy souborů uzavřené v uvozovkách s názvy souborů uzavřenými v ostrých závorkách. Například uděleno výše uvedených dvou **include_alias – #pragma** direktivy kompilátoru provádí následující žádné nahrazení `#include` direktivy:

```cpp
#include <api.h>
#include "stdio.h"
```

Následující direktiva dále způsobí chybu:

```cpp
#pragma include_alias(<header.h>, "header.h")  // Error
```

Všimněte si, že ohlásil název souboru v chybových zprávách, nebo jako hodnotu předdefinovanou **&#95; &#95;soubor&#95; &#95;** makro, je název souboru po provedení nahrazování. Například po následující direktivy zobrazit výstup:

```cpp
#pragma include_alias( "VeryLongFileName.H", "myfile.h" )
#include "VeryLongFileName.H"
```

K chybě v VERYLONGFILENAME. H vytvoří se následující chybová zpráva:

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