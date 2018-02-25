---
title: "#řádek – direktiva (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 10/18/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- '#line'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13760aa7c503339c16ed6418badc295170d2c938
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="line-directive-cc"></a>#line – direktiva (C++)

Direktiva `#line` přikazuje preprocesoru, aby změnil interně uložená čísla řádků a název souboru kompilátoru na zadaná čísla řádků a název souboru.

## <a name="syntax"></a>Syntaxe

> **#line** *číslice pořadí* ["*filename*"]

## <a name="remarks"></a>Poznámky

Kompilátor používá číslo řádku a volitelný název souboru pro odkazování na chyby, které zjistí během kompilace. Číslo řádku obvykle odkazuje na aktuální vstupní řádek a název souboru odkazuje na aktuální vstupní soubor. Číslo řádku se zvyšuje po zpracování každého řádku.

*Číslice pořadí* hodnota může být jakékoli celočíselná konstanta. Nahrazení makrem lze provést u tokenů předběžného zpracování, ale výsledek musí být vyhodnocen na správnou syntaxi. *Filename* může být libovolnou kombinací znaků a musí být uzavřena v uvozovkách (**""**). Pokud *filename* je tento parametr vynechán, předchozí filename zůstává beze změny.

Zapsáním direktivy `#line` je možné změnit číslo zdrojového řádku a název souboru. Překladač používá číslo řádku a název souboru k určení hodnoty předdefinovaná makra **&#95; &#95; SOUBOR &#95; &#95;**  a **&#95; &#95; Řádek &#95; &#95;** . Makra je možné použít k vložení samopopisných chybových zpráv do textu programu. Další informace o těchto předdefinovaná makra najdete v tématu [předdefinovaná makra](../preprocessor/predefined-macros.md).

**&#95; &#95; SOUBOR &#95; &#95;**  makro rozšíří na řetězec, jehož obsah je název souboru v uvozovkách (**""**).

Při změně čísla řádku a názvu souboru ignoruje kompilátor předchozí hodnoty a pokračuje ve zpracování s novými hodnotami. Direktiva `#line` je obvykle používána generátory programu pro odkazování chybových zpráv na původní zdrojový soubor namísto generovaného programu.

Následující příklady ilustrují `#line` a **&#95; &#95; Řádek &#95; &#95;**  a **&#95; &#95; SOUBOR &#95; &#95;**  makra.

V tomto prohlášení číslo řádku interně uložené nastavena na 151 a název souboru se změní na copy.c.

```cpp
#line 151 "copy.c"
```

 V tomto příkladu makro `ASSERT` používá předdefinovaná makra **&#95; &#95; Řádek &#95; &#95;**  a **&#95; &#95; SOUBOR &#95; &#95;**  pro tisk chybovou zprávu o zdrojový soubor, pokud daný assertion není pravda.

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)