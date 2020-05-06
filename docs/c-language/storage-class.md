---
title: Třída úložiště
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: aa6e977b3aa03b5f08901cfa8b0abe1b4046e72d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857005"
---
# <a name="storage-class"></a>Třída úložiště

Specifikátor třídy úložiště v definici funkce poskytuje funkci buď `extern` nebo **statickou** třídu úložiště.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory*<sub>opt</sub> *atribut – seq*<sub>opt</sub> *deklarátor* *deklarace-list*<sub>opt</sub> – *složený* příkaz

/\**atribut – seq* je specifický pro společnost Microsoft\*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*Storage-Class-specifikátor*:/\* pro definice funkcí\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**tras**

Pokud definice funkce nezahrnuje *specifikátor třídy úložiště*, je výchozí hodnotou třídy úložiště `extern`. Funkci lze explicitně deklarovat jako `extern`, není to však zapotřebí.

Pokud deklarace funkce obsahuje `extern` *specifikátor třídy úložiště* , má identifikátor stejné propojení jako jakákoli viditelná deklarace identifikátoru s rozsahem souboru. Pokud v oboru souboru neexistuje žádná viditelná deklarace, má identifikátor vnější propojení. Pokud identifikátor má rozsah souboru a žádný *specifikátor třídy úložiště*, má identifikátor vnější propojení. Vnější propojení znamená, že všechny instance identifikátoru označují stejný objekt nebo funkci. Další informace o propojení a rozsahu souboru naleznete v tématu [Doba života, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) .

Deklarace funkcí v oboru bloku se specifikátorem třídy úložiště jiným než `extern` generují chyby.

Funkce s třídou **statického** úložiště je viditelná pouze ve zdrojovém souboru, ve kterém je definována. Všechny ostatní funkce s třídou úložiště `extern` zadanou explicitně či implicitně jsou viditelné ve všech zdrojových souborech programu. Pokud je požadována **statická** třída úložiště, musí být deklarována v prvním výskytu deklarace (pokud existuje) funkce a v definici funkce.

**Specifické pro Microsoft**

Pokud jsou rozšíření společnosti Microsoft povolena, je funkce, která byla původně deklarována bez třídy úložiště `extern` (nebo s třídou úložiště), dána třídou **statického** úložiště, pokud je definice funkce ve stejném zdrojovém souboru a pokud definice explicitně určuje třídu **statického** úložiště.

Je-li program kompilován s možností kompilátoru /Ze, funkce deklarované uvnitř bloku pomocí klíčového slova `extern` mají globální viditelnost. To neplatí v případě kompilace s možností /Za. Tato funkce nemusí být spolehlivá, bere-li se v úvahu přenositelnost zdrojového kódu.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
