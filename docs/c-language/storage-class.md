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
ms.openlocfilehash: d5664634687c689316427c8652865ba9423e24f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157914"
---
# <a name="storage-class"></a>Třída úložiště

Specifikátor třídy úložiště v definici funkce poskytuje funkci `extern` nebo **statické** třídu úložiště.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*<sub>optimalizované</sub> *sekvence atributů*<sub>optimalizované</sub> *deklarátor* *seznam deklarací*  <sub>optimalizované</sub> *compound-statement*

/\* *sekvence atributů* je specifické pro Microsoft \*/

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*Storage-class-specifier*: /\* pro definice funkcí \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statická**

Pokud neobsahuje definici funkce *storage-class-specifier*, výchozí hodnota třídy úložiště `extern`. Funkci lze explicitně deklarovat jako `extern`, není to však zapotřebí.

Pokud obsahuje deklarace funkce *storage-class-specifier* `extern`, má identifikátor stejné propojení jako jakákoli viditelná deklarace identifikátoru s rozsahem souboru. Pokud v oboru souboru neexistuje žádná viditelná deklarace, má identifikátor vnější propojení. Pokud nemá identifikátor rozsahu souboru ale žádné *storage-class-specifier*, má identifikátor vnější propojení. Vnější propojení znamená, že všechny instance identifikátoru označují stejný objekt nebo funkci. Zobrazit [životnost, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) Další informace o propojení a oboru souboru.

Deklarace funkcí v oboru bloku se specifikátorem třídy úložiště jiným než `extern` generují chyby.

Funkce s **statické** třídu úložiště je viditelná pouze ve zdrojovém souboru, ve kterém je definována. Všechny ostatní funkce s třídou úložiště `extern` zadanou explicitně či implicitně jsou viditelné ve všech zdrojových souborech programu. Pokud **statické** třídy úložiště se požaduje, musí být deklarován v prvním výskytu deklarace funkce (pokud existuje) a v její definici funkce.

**Microsoft Specific**

Pokud jsou povolena rozšíření společnosti Microsoft, funkce původně deklarovaná bez třídy úložiště (nebo s `extern` třídy úložiště) dostane **statické** třída úložiště, pokud definice funkce umístěna ve stejném zdrojovém souboru a pokud definice explicitně určuje **statické** třídu úložiště.

Je-li program kompilován s možností kompilátoru /Ze, funkce deklarované uvnitř bloku pomocí klíčového slova `extern` mají globální viditelnost. To neplatí v případě kompilace s možností /Za. Tato funkce nemusí být spolehlivá, bere-li se v úvahu přenositelnost zdrojového kódu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
