---
title: '#řádek – direktiva (C++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: ad0fe1514e89b861bab046652b1768862cc8045b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59023734"
---
# <a name="line-directive-cc"></a>#line – direktiva (C++)

**#Line** – direktiva určuje preprocesoru, chcete-li změnit na zadaná čísla řádků a název souboru kompilátoru interně uložená čísla řádků a název souboru.

## <a name="syntax"></a>Syntaxe

> **#line** *sekvence číslic* ["*filename*"]

## <a name="remarks"></a>Poznámky

Kompilátor používá číslo řádku a volitelný název souboru pro odkazování na chyby, které zjistí během kompilace. Číslo řádku obvykle odkazuje na aktuální vstupní řádek a název souboru odkazuje na aktuální vstupní soubor. Číslo řádku se zvyšuje po zpracování každého řádku.

*Sekvence číslic* hodnota může být jakákoli celočíselná konstanta. Nahrazení makrem lze provést u tokenů předběžného zpracování, ale výsledek musí být vyhodnocen na správnou syntaxi. *Filename* může být libovolná kombinace znaků a musí být uzavřen do dvojitých uvozovek (**""**). Pokud *filename* je tento parametr vynechán, předchozí název souboru zůstane beze změny.

Je možné změnit číslo zdrojového řádku a název souboru zápisem **#line** směrnice. Překladač používá číslo řádku a název souboru k určení hodnot předdefinovaných maker `__FILE__` a `__LINE__`. Makra je možné použít k vložení samopopisných chybových zpráv do textu programu. Další informace o těchto předdefinovaných makrech naleznete v tématu [předdefinovaná makra](../preprocessor/predefined-macros.md).

`__FILE__` – Makro rozšíří na řetězec, jehož obsahem je název souboru uzavřený v dvojitých uvozovkách (**""**).

Při změně čísla řádku a názvu souboru ignoruje kompilátor předchozí hodnoty a pokračuje ve zpracování s novými hodnotami. **#Line** – direktiva je obvykle používána generátory programu chybových zpráv pro odkazování na původní zdrojový soubor namísto generovaného programu.

Následující příklady znázorňují **#line** a `__LINE__` a `__FILE__` makra.

V tomto příkazu je interně uložené číslo nastaveno na 151 a název souboru se změní na copy.c.

```cpp
#line 151 "copy.c"
```

V tomto příkladu makro `ASSERT` používá předdefinovaná makra `__LINE__` a `__FILE__` pro tisk chybové zprávy o zdrojovém souboru, pokud daný kontrolní výraz není pravda.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Viz také:

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)