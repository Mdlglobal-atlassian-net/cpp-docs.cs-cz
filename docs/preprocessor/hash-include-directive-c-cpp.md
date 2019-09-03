---
title: '#include – direktiva (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 0792f522427e5658de992969745878894fbd454d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220258"
---
# <a name="include-directive-cc"></a>#include direktiva (CC++/)

Říká preprocesoru, aby považoval obsah zadaného souboru, jako by se zobrazil ve zdrojovém programu v místě, kde se nachází direktiva.

## <a name="syntax"></a>Syntaxe

> **#include** "*cesta-specifikace*" \
> **#include** *cesta – specifikace* \<>

## <a name="remarks"></a>Poznámky

Můžete uspořádat definice konstanty a makra do souborů include a potom použít direktivy **#include** pro jejich přidání do libovolného zdrojového souboru. Zahrnuté soubory jsou také užitečné pro zahrnutí deklarací externích proměnných a komplexních datových typů. Typy lze definovat a pojmenovat pouze jednou v vloženém souboru vytvořeném pro tento účel.

*Cesta-specifikace* je název souboru, který může volitelně předcházet specifikace adresáře. Název souboru musí pojmenovat existující soubor. Syntaxe *specifikace cesty* závisí na operačním systému, ve kterém je program zkompilován.

Informace o tom, jak odkazovat na sestavení v C++ aplikaci, která je zkompilována pomocí [/CLR](../build/reference/clr-common-language-runtime-compilation.md), naleznete v tématu [#using](../preprocessor/hash-using-directive-cpp.md).

Obě formy syntaxe způsobí nahrazení této direktivy celým obsahem zadaného souboru include. Rozdíl mezi těmito dvěma formuláři je pořadí, ve kterém preprocesor vyhledává soubory hlaviček, pokud je cesta zadána neúplně. V následující tabulce je uveden rozdíl mezi dvěma formami syntaxe.

|Forma syntaxe|Akce|
|---|------------|
|Citovaný formulář|Preprocesor vyhledává zahrnuté soubory v tomto pořadí:<br/><br/> 1) ve stejném adresáři jako soubor, který obsahuje příkaz **#include** .<br/><br/> 2) v adresářích aktuálně otevřených vložených souborů v obráceném pořadí, v jakém byly otevřeny. Hledání začíná v adresáři nadřazeného vloženého souboru a pokračuje směrem nahoru přes adresáře všech souborů include.<br/><br/> 3) na cestě určené každou možností kompilátoru **/i** .<br/><br/> 4) podél cest, které jsou určeny proměnnou prostředí INCLUDE.|
|Formulář lomené závorky|Preprocesor vyhledává zahrnuté soubory v tomto pořadí:<br/><br/> 1) na cestě určené každou možností kompilátoru **/i** .<br/><br/> 2) při kompilování proběhne na příkazovém řádku, podél cest, které jsou určeny proměnnou prostředí INCLUDE.|

Preprocesor zastaví hledání, jakmile nalezne soubor s daným názvem. Pokud uzavřete úplnou, nejednoznačnou specifikaci cesty pro soubor include mezi dvojité uvozovky (`" "`), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.

Pokud je název souboru, který je uzavřen v uvozovkách, nekompletní specifikací cesty, preprocesor nejprve prohledá adresář "nadřazeného" souboru. Nadřazený soubor je soubor, který obsahuje direktivu **#include** . Pokud například zahrnete soubor s názvem *soubor2* do souboru s názvem *Soubor1*, bude nadřazeným souborem *Soubor1* .

Soubory zahrnutí můžou být "vnořené": Direktiva **#include** se může objevit v souboru, který je pojmenován jinou direktivou **#include** . Například *soubor2* může zahrnovat *file3*. V tomto případě by byl příkaz *Soubor1* stále nadřazený z *soubor2*, ale bude to "prarodič" *file3*.

Pokud jsou vložené soubory vnořené a při kompilaci dojde v příkazovém řádku, hledání adresáře začíná v adresářích nadřazeného souboru. Pak projde adresáři všech souborů. To znamená, že vyhledávání začíná relativně vzhledem k adresáři obsahujícímu zdroj, který se právě zpracovává. Pokud soubor není nalezen, hledání se přesune do adresáře, které jsou zadány pomocí možnosti kompilátoru [/i (další adresáře include)](../build/reference/i-additional-include-directories.md) . Nakonec se prohledávají adresáře, které jsou určeny proměnnou prostředí INCLUDE.

Ve vývojovém prostředí sady Visual Studio je proměnná prostředí INCLUDE ignorována. Informace o tom, jak nastavit adresáře, ve kterých se vyhledávají vložené soubory a soubory knihovny, najdete na [stránce vlastností adresářů VC + +](../build/reference/vcpp-directories-property-page.md).

Tento příklad ukazuje zahrnutí souborů pomocí lomených závorek:

```C
#include <stdio.h>
```

Tento příklad přidá obsah souboru s názvem STDIO. H ke zdrojovému programu. Lomené závorky způsobí, že preprocesor vyhledá v adresářích, které jsou určeny proměnnou prostředí INCLUDE pro STDIO. H po prohledání adresářů určených parametrem kompilátoru **/i** .

Následující příklad ukazuje zahrnutí souboru pomocí citovaného formuláře:

```C
#include "defs.h"
```

Tento příklad přidá obsah souboru zadaného parametrem DEFS. H ke zdrojovému programu. Uvozovky znamenají, že preprocesor nejprve prohledá adresář obsahující nadřazený zdrojový soubor.

Vnoření souborů zahrnutí může pokračovat až na 10 úrovní. Když je zpracována vnořená **#include** , preprocesor pokračuje v vkládání nadřazeného souboru include do původního zdrojového souboru.

**Specifické pro společnost Microsoft**

Chcete-li najít zdrojové soubory zahrnutelných, preprocesor nejprve prohledá adresáře, které jsou určeny možností kompilátoru **/i** . Pokud parametr **/i** není k dispozici, nebo pokud se nepovede, preprocesor používá PROMĚNNOU prostředí include k vyhledání všech vložených souborů v lomených závorkách. Proměnná prostředí INCLUDE a možnost kompilátoru **/i** může obsahovat několik cest oddělených středníky ( **;** ). Pokud se více než jeden adresář zobrazuje jako součást parametru **/i** nebo v rámci proměnné prostředí include, preprocesor je vyhledá v pořadí, ve kterém se zobrazí.

Například příkaz

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

způsobí, že preprocesor vyhledá v adresáři D:\MSVC\INCLUDE\ pro zahrnuté soubory, jako je například STDIO. Y. Příkazy

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

mají stejný účinek. V případě, že obě sady hledání selžou, je vygenerována závažná chyba kompilátoru.

Pokud je název souboru plně zadaný pro soubor zahrnutí, který má cestu, která obsahuje dvojtečku (například F:\MSVC\SPECIAL\INCL\TEST. H), preprocesor sleduje cestu.

Pro zahrnuté soubory, které jsou `#include "path-spec"`zadány jako, začíná hledání adresáře adresářem nadřazeného souboru a pak pokračuje přes adresáře všech souborů prarodičů. To znamená, že vyhledávání začíná relativně k adresáři, který obsahuje zdrojový soubor obsahující direktivu **#include** , která je zpracovávána. Pokud neexistuje žádný soubor @ a soubor nebyl nalezen, hledání pokračuje, jako by název souboru byl uzavřen do lomených závorek.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)\
[/I (další adresáře k zahrnutí)](../build/reference/i-additional-include-directories.md)
