---
title: Souhrn gramatiky preprocesoru (C/C++)
description: Definuje a popisuje gramatickou syntaxi preprocesoru jazyka Microsoft C/C++ kompilátor (MSVC).
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 68e5f09acfc6444afb46bcbc0f7e9db10b04afed
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076873"
---
# <a name="preprocessor-grammar-summary-cc"></a>Souhrn gramatiky preprocesoru (C/C++)

Tento článek popisuje formální gramatiku jazyka C a C++ preprocesoru. Zabývá se syntaxí direktiv předzpracování a operátorů. Další informace naleznete v tématu direktivy [preprocesoru](../preprocessor/preprocessor.md) a [direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md).

## <a name="definitions-for-the-grammar-summary"></a><a name="definitions"></a>Definice pro Shrnutí gramatiky

Terminály jsou koncové body v definici syntaxe. Žádné jiné řešení není možné. Terminály obsahují sadu vyhrazených slov a uživatelské identifikátory.

Neterminály jsou zástupné symboly v syntaxi. Většina je definována jinde v tomto souhrnu syntaxe. Definice mohou být rekurzivní. Následující neterminály jsou definovány v části [lexikální konvence](../cpp/lexical-conventions.md) v  *C++ referenční příručce jazyka*:

*konstanta*, *konstantní výraz*, *identifikátor*, *klíčové slovo*, *operátor*, *punctuator*

Volitelná součást je označena jako volitelná. <sub>opt</sub> Například následující syntaxe označuje volitelný výraz uzavřený ve složených závorkách:

**{** *Expression*<sub>opt</sub> **}**

## <a name="document-conventions"></a><a name="conventions"></a>Konvence dokumentů

Úmluvy používají odlišné atributy písma pro různé součásti syntaxe. Symboly a písma jsou následující:

| Atribut | Popis |
|---------------|-----------------|
| *neterminálu* | Kurzíva označuje neterminály. |
| **#include** | Terminály tučného typu jsou slova a symboly vyhrazená literály, které je nutné zadat tak, jak je znázorněno. Znaky v tomto kontextu vždy rozlišují velká a malá písmena. |
| <sub>přihlásit</sub> | Neterminály následované <sub>výslovným souhlasem</sub> jsou vždycky volitelné.|
| výchozí písmo | Znaky ze sady, které jsou popsány nebo uvedeny v tomto písmu, lze použít jako terminály v příkazech. |

Dvojtečka ( **:** ) po neterminálu zavádí svou definici. Alternativní definice jsou uvedeny na samostatných řádcích.

V blocích syntaxe kódu mají tyto symboly ve výchozím řezu písma zvláštní význam:

| Písmeno | Popis |
|---|---|
| \[] | Hranaté závorky obklopí volitelný prvek. |
| {\|} | Složené závorky ohraničují alternativní prvky oddělené svislými pruhy. |
| Tlačítka ... | Určuje, že se může opakovat vzor předchozího prvku. |

V blocích syntaxe kódu, čárky (`,`), tečky (`.`), dvojtečky (`;`), dvojtečky (`:`), kulaté závorky (`( )`), dvojité uvozovky (`"`) a jednoduché uvozovky (`'`) jsou literály.

## <a name="preprocessor-grammar"></a><a name="grammar"></a>Gramatika preprocesoru

*řídicí čára*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** tokenu *identifikátoru ID* *-řetězec*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identifikátor* **(** *ID*<sub>opt</sub> **,** ... **,** *identifier*<sub>opt</sub> **identifikátor)** *token-* \<sub>opt</sub>
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _cesta-specifikace_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _cesta-specifikace_ **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *Číselná sekvence* **"** _filename_ **"** <sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token-řetězec*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-řetězec*

*konstantní výraz*: \
&nbsp;&nbsp;&nbsp;&nbsp;**definovány (** *identifikátor* **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**definovaný** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp;všech ostatních konstantních výrazů

*podmíněné*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-Part* *elif – část*<sub>opt</sub> *Else*-<sub>Part opt</sub> *endif-line*

*if-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*text* *if-line*

*řádek if-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *konstantního výrazu*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identifikátor*\
&nbsp;&nbsp;&nbsp;*identifikátor* &nbsp; **#ifndef**

*elif – části*: \
&nbsp;&nbsp;&nbsp;&nbsp;*text* *na řádku elif*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif-Parts* *elif-line* *text*

*elif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *konstantní výraz*

*Else – část*: \
&nbsp;&nbsp;&nbsp;*textu* &nbsp;*Else řádku*

*Else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*sekvence číslic*: \
&nbsp;&nbsp;&nbsp;&nbsp;*číslice*\
&nbsp;&nbsp;&nbsp;&nbsp;*číslice* *s pořadovým číslem číslice*

*číslice*: jedna z těchto \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*řetězec tokenu*: \
&nbsp;&nbsp;&nbsp;&nbsp;ch řetězců tokenů

*token*: \
&nbsp;&nbsp;&nbsp;*klíčová slova* &nbsp;\
&nbsp;&nbsp;&nbsp;*identifikátor* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*konstanta*\
&nbsp;&nbsp;&nbsp;*operátor* &nbsp;\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*název souboru*: \
&nbsp;&nbsp;&nbsp;&nbsp;platný název souboru operačního systému

*cesta-specifikace*: \
&nbsp;&nbsp;&nbsp;&nbsp;platná cesta k souboru

*text*: \
&nbsp;&nbsp;&nbsp;&nbsp;libovolné sekvenci textu

> [!NOTE]
> Následující neterminály jsou rozbaleny v části [lexikální konvence](../cpp/lexical-conventions.md) v  *C++ odkazu na jazyk*: *konstanta*, *konstantní výraz*, *identifikátor*, *klíčové slovo*, *operátor*a *punctuator*.

## <a name="see-also"></a>Viz také

[C/C++ reference preprocesoru](../preprocessor/c-cpp-preprocessor-reference.md)
