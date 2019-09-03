---
title: '#line – direktiva (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220226"
---
# <a name="line-directive-cc"></a>#line direktiva (CC++/)

Direktiva **#line** přikáže preprocesoru ke změně interního uloženého čísla řádku a názvu souboru kompilátoru na dané číslo řádku a název souboru.

## <a name="syntax"></a>Syntaxe

> **#line** *sekvence číslic* ["*filename*"]

## <a name="remarks"></a>Poznámky

Kompilátor používá číslo řádku a volitelný název souboru pro odkazování na chyby, které zjistí během kompilace. Číslo řádku obvykle odkazuje na aktuální vstupní řádek a název souboru odkazuje na aktuální vstupní soubor. Číslo řádku se zvyšuje po zpracování každého řádku.

Hodnota *pořadí číslic* může být libovolná celočíselná konstanta. Nahrazení makrem lze provést u tokenů předběžného zpracování, ale výsledek musí být vyhodnocen na správnou syntaxi. *Název souboru* může být libovolná kombinace znaků a musí být uzavřen do dvojitých uvozovek (`" "`). Pokud je *název souboru* vynechán, předchozí název souboru zůstane beze změny.

Zápisem direktivy **#line** můžete změnit číslo a název souboru zdrojového řádku. Překladatel používá číslo řádku a název souboru k určení hodnot předdefinovaných maker `__FILE__` a. `__LINE__` Makra je možné použít k vložení samopopisných chybových zpráv do textu programu. Další informace o těchto předdefinovaných makrech naleznete v tématu [Předdefinovaná makra](../preprocessor/predefined-macros.md).

Makro se rozšíří na řetězec, jehož obsah je název souboru, který je ohraničen dvojitými uvozovkami (`" "`). `__FILE__`

Při změně čísla řádku a názvu souboru ignoruje kompilátor předchozí hodnoty a pokračuje ve zpracování s novými hodnotami. Direktiva **#line** obvykle používá generátory programů k vygenerování chybových zpráv pro odkazování na původní zdrojový soubor místo na vygenerovaný program.

Následující příklady ilustrují **#line** a `__LINE__` makra a `__FILE__` .

V tomto příkazu je interně uložené číslo řádku nastaveno na 151 a název souboru je změněn na Kopírovat. c.

```C
#line 151 "copy.c"
```

V tomto příkladu makro `ASSERT` používá Předdefinovaná makra `__LINE__` a `__FILE__` k tisku chybové zprávy o zdrojovém souboru, pokud daný kontrolní výraz není pravdivý.

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Viz také:

[Direktivy preprocesoru](../preprocessor/preprocessor-directives.md)
