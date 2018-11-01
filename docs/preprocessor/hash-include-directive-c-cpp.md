---
title: '##include – direktiva (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 3cf595fd8f519706f43ad70c4cdddf0297c8149e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492531"
---
# <a name="include-directive-cc"></a>#include – direktiva (C++)
Určuje preprocesoru, aby s obsahem zadaného souboru, jak by se měl nacházet ve zdrojové aplikaci v místě, kde se objeví direktiva.

## <a name="syntax"></a>Syntaxe

```
#include  "path-spec"
#include  <path-spec>
```

## <a name="remarks"></a>Poznámky

Můžete uspořádat definice konstanty a makra v zahrnutých souborech a potom pomocí **#include** direktivy je přidejte do libovolného zdrojového souboru. Zahrnout soubory jsou také užitečná pro zahrnutí deklarace externích proměnných a komplexních datových typů. Typy může být definované a pojmenovat pouze jednou v zahrnutém souboru vytvořeném pro tento účel.

`path-spec` Je název souboru, který může být volitelně předcházen specifikací adresáře. Název souboru musí být název existujícího souboru. Syntaxe `path-spec` závisí na operačním systému, ve kterém je program zkompilován.

Informace o tom, jak odkazovat na sestavení v C++ aplikaci zkompilované s použitím [/CLR](../build/reference/clr-common-language-runtime-compilation.md), naleznete v tématu [#using](../preprocessor/hash-using-directive-cpp.md).

Obě formy syntaxe způsobí náhradu této direktivy celým obsahem určeného zahrnutého souboru se nahradí. Rozdíl mezi dvěma formuláři je v tom pořadí, ve kterém preprocesor hledá soubory hlaviček případě je cesta zadána neúplně. Následující tabulka ukazuje rozdíl mezi dvě různými formami syntaxe.

|Forma syntaxe|Akce|
|-----------------|------------|
|Citovaný formulář|Preprocesor vyhledává zahrnuté soubory v tomto pořadí:<br /><br /> (1) ve stejném adresáři jako soubor, který obsahuje **#include** příkazu.<br /><br /> (2) v adresářích aktuálně otevřeném zahrňte soubory v obráceném pořadí, v jakém byly otevřeny. Hledání začne v adresáři nadřazeného souboru zahrnutí a pokračuje směrem nahoru přes adresáře všech nadřazených soubory k zahrnutí.<br /><br /> (3) v cestě, která je zadána každý `/I` – možnost kompilátoru.<br /><br /> 4)<br /><br /> Podél cest, které jsou určeny proměnnou prostředí INCLUDE.|
|Forma lomené závorky|Preprocesor vyhledává zahrnuté soubory v tomto pořadí:<br /><br /> (1) v cestě, která je zadána každý `/I` – možnost kompilátoru.<br /><br /> (2) při kompilaci na příkazovém řádku, podél cest, které jsou určeny proměnnou prostředí INCLUDE.|

Preprocesor zastaví hledání, jakmile nalezne soubor s daným názvem. Pokud zadáte jednoznačnou, kompletní cesta specifikace k souboru include mezi dvojité uvozovky (""), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.

Pokud je název souboru uzavřený do dvojitých uvozovek specifikace neúplné cesty, preprocesor nejprve prohledá "rodičovský" adresář. Nadřazený soubor je soubor, který obsahuje **#include** směrnice. Například pokud zahrnete soubor s názvem `file2` do souboru s názvem `file1`, `file1` je nadřazený soubor.

Zahrnuté soubory mohou být "vnořené"; To znamená **#include** – direktiva se mohou objevit v souboru pojmenovaným jiným **#include** směrnice. Například `file2` může zahrnovat `file3`. V takovém případě `file1` stále by šlo nadřazený `file2`, ale bylo by "nadřazený" z `file3`.

Při vnoření souborů a jsou při kompilaci na příkazovém řádku, hledání začne s adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů výše nadřazených. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdroj, který se právě zpracovává. Pokud soubor není nalezen, hledání se přesune do adresáře, které jsou určeny `/I` – možnost kompilátoru. Nakonec jsou prohledány adresáře určené proměnnou prostředí INCLUDE.

Z vývojového prostředí je proměnná prostředí INCLUDE ignorována. Informace o tom, jak nastavit adresáře, které se budou hledat vkládané soubory – to platí také pro proměnné prostředí LIB – viz [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md).

Tento příklad ukazuje začlenění souboru pomocí ostrých závorek:

```
#include <stdio.h>
```

V tomto příkladu přidá obsah souboru s názvem STDIO. H do zdrojového programu. Lomené závorky způsobí, že preprocesor hledat adresáře určené proměnnou prostředí INCLUDE pro STDIO. H po prohledání adresářů uvedených `/I` – možnost kompilátoru.

Následující příklad ukazuje začlenění souboru pomocí citovaného formuláře:

```
#include "defs.h"
```

V tomto příkladu přidá obsah souboru určeného DEFS. H do zdrojového programu. Uvozovky znamenají, že preprocesor nejprve prohledá adresář obsahující nadřazený zdrojový soubor.

Vnoření vložených souborů může pokračovat až do 10 úrovně. Když ve vnořeném **#include** je zpracována, bude preprocesor nadále vkládat vnořené soubory do původního zdrojového souboru.

**Specifické pro Microsoft**

Pro nalezení zahrnutelných zdrojových souborů, že preprocesor nejprve prohledá adresáře, které jsou určeny `/I` – možnost kompilátoru. Pokud `/I` možnost není k dispozici nebo se nezdaří, preprocesor použije proměnnou prostředí INCLUDE k nalezení všech souborů include v lomených závorkách. Proměnná prostředí INCLUDE a `/I` – možnost kompilátoru může obsahovat několik cest oddělených středníky (;). Pokud více než jeden adresář zobrazí jako součást `/I` možnost nebo v rámci proměnná prostředí INCLUDE, preprocesor je hledá v pořadí, v jakém jsou uvedeny.

Například příkaz

```
CL /ID:\MSVC\INCLUDE MYPROG.C
```

způsobí, že bude preprocesor hledat zahrnuté soubory, jako je například STDIO adresáři D:\MSVC\INCLUDE\. H. Příkazy

```
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

mají stejný účinek. Pokud se obě sady vyhledávání nezdaří, je generována závažná chyba kompilátoru.

Pokud název souboru je plně zadaný pro soubor include, který má cestu, která obsahuje dvojtečkou (například F:\MSVC\SPECIAL\INCL\TEST. H), preprocesor sleduje cestu.

Při zahrnutí souborů, které jsou určeny jako `#include` "`path-spec`", hledání začne adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů výše nadřazených. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdroj souboru, který obsahuje **#include** směrnice, které jsou zpracovávány. Pokud není žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání pokračuje, jako by název souboru byl uzavřen do lomených závorek.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)