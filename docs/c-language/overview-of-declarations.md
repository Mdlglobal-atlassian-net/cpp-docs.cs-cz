---
title: Přehled deklarací
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 0ffda6522e632533b0aaa4ba146e8fad082ed435
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857057"
---
# <a name="overview-of-declarations"></a>Přehled deklarací

Deklarace určuje interpretaci a atributy sady identifikátorů. Deklarace, která také způsobí, že úložiště je rezervováno pro objekt nebo funkci s názvem identifikátor se nazývá "definice". Deklarace C pro proměnné, funkce a typy mají tuto syntaxi:

## <a name="syntax"></a>Syntaxe

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – atribut specifikátors* *-SEQ*<sub>opt</sub> *init-deklarátor-list*<sub>opt</sub>**;**

/\**atribut-seq*<sub>opt</sub> je specifický pro společnost Microsoft */

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*init-deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor-list* **,** *init-deklarátor*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicializátor* deklarátor

> [!NOTE]
> Tato syntaxe *deklarace* se neopakuje v následujících oddílech. Syntaxe v následujících oddílech obvykle začíná *deklarátor* neterminálem.

Deklarace v *seznamu init-deklarátor-list* obsahují identifikátory s názvem; *init* je zkratka pro inicializátor. *Init-deklarátor-list* je sekvence deklarátory oddělená čárkami, každá z nich může mít další informace o typu, nebo inicializátor nebo obojí. *Deklarátor* obsahuje identifikátory, pokud jsou deklarovány. Neterminálové *specifikátory deklarace* se skládají ze sekvence typu a specifikátorů třídy úložiště, které označují propojení, dobu trvání úložiště a alespoň část typu entit, které deklarátory označuje. Deklarace se proto skládají z některé kombinace specifikátorů třídy úložiště, specifikátorů typu, kvalifikátorů typu, deklarátory a inicializátorů.

Deklarace mohou obsahovat jeden nebo více volitelných atributů uvedených v *atributu-SEQ*; *SEQ* je zkratka pro sekvenci. Tyto atributy specifické pro společnost Microsoft provádějí celou řadu funkcí, které jsou podrobně popsány v celé této příručce.

V obecné formě deklarace proměnné *typ specifikátor* poskytuje datový typ proměnné. *Specifikátor typu* může být složený, jako když je typ upraven pomocí **const** nebo `volatile`. `declarator` Obsahuje název proměnné, případně změněno k deklaraci pole nebo typu ukazatele. Například:

```C
int const *fp;
```

deklaruje proměnnou s názvem `fp` jako ukazatel na hodnotu neupravitelné (**const**). `int` V deklaraci můžete definovat více než jednu proměnnou pomocí více deklarátory, oddělených čárkami.

Deklarace musí mít alespoň jeden deklarátor, nebo jeho specifikátor typu musí deklarovat značku struktury, značku sjednocení nebo členy výčtu. Deklarátory poskytují jakékoli zbývající informace o identifikátoru. Deklarátor je identifikátor, který lze upravit pomocí hranatých závorek (**[]**), hvězdičky<strong>\*</strong>() nebo závorek ( **()** ) pro deklaraci pole, ukazatele nebo typu funkce v uvedeném pořadí. Při deklaraci jednoduchých proměnných (jako jsou znak, celé číslo a plovoucí desetinné čárky) nebo struktur a sjednocení jednoduchých proměnných `declarator` je pouze identifikátor. Další informace o deklarátory naleznete v tématu [deklarace deklarátory a proměnných](../c-language/declarators-and-variable-declarations.md).

Všechny definice jsou implicitně deklarace, ale ne všechny deklarace jsou definice. Například deklarace proměnných, které začínají specifikátorem třídy `extern` úložiště, jsou "odkazující" "místo" definování "deklarací. Pokud je externí proměnná označována před definováním, nebo pokud je definována v jiném zdrojovém souboru, než který je použit, `extern` deklarace je nezbytná. Úložiště není přidělené deklaracemi, které neodkazují, ani proměnné se v deklaracích nedají inicializovat.

V deklaracích proměnných je vyžadována třída úložiště nebo typ (nebo obojí). `__declspec`S výjimkou je povolen pouze jeden specifikátor třídy úložiště v deklaraci a ne všechny specifikátory třídy úložiště jsou povoleny v každém kontextu. Třída `__declspec` úložiště je povolena s dalšími specifikátory třídy úložiště a je povolena více než jednou. Specifikátor třídy úložiště deklarace má vliv na to, jak je deklarovaná položka uložená a inicializovaná a které části programu mohou odkazovat na položku.

Koncoví *specifikátory třídy úložiště* definované v jazyce C zahrnují **auto**, `extern`, **Register**, **static**a `typedef`. Kromě toho Microsoft C zahrnuje terminál `__declspec` *specifikátoru úložiště* . Všechny terminály *specifikátoru třídy úložiště* s `typedef` výjimkou a `__declspec` jsou popsány v tématu [třídy úložiště](../c-language/c-storage-classes.md). Informace o `typedef`naleznete v tématu [deklarace typedef](../c-language/typedef-declarations.md) . Informace o nástroji `__declspec`najdete v tématu [Rozšířené atributy třídy úložiště](../c-language/c-extended-storage-class-attributes.md) .

Umístění deklarace v rámci zdrojového programu a přítomnost nebo absence jiných deklarací proměnné představují důležité faktory při určování životnosti proměnných. Může existovat více změněných deklarací, ale pouze jedna definice. Definice se ale může objevit ve více než jedné jednotce překladu. U objektů s interní vazbou se toto pravidlo vztahuje samostatně na každou jednotku překladu, protože interně propojené objekty jsou jedinečné pro jednotku překladu. Pro objekty s vnějším propojením se toto pravidlo vztahuje na celý program. Další informace o viditelnosti najdete v tématu [Doba života, rozsah, viditelnost a propojení](../c-language/lifetime-scope-visibility-and-linkage.md) .

Specifikátory typu poskytují některé informace o datových typech identifikátorů. Výchozí specifikátor typu je `int`. Další informace naleznete v tématu [specifikátory typu](../c-language/c-type-specifiers.md). Specifikátory typu mohou také definovat značky typů, struktury a sjednocení názvy komponent a výčty výčtu. Další informace najdete v tématu [deklarace výčtu](../c-language/c-enumeration-declarations.md), [deklarace struktury](../c-language/structure-declarations.md)a [deklarace sjednocení](../c-language/union-declarations.md).

Existují dva terminály *kvalifikátoru typu* : **const** a `volatile`. Tyto kvalifikátory určují další vlastnosti typů, které jsou relevantní pouze při přístupu k objektům daného typu prostřednictvím l-Values. Další informace o **const** a `volatile`naleznete v tématu [kvalifikátory typu](../c-language/type-qualifiers.md). Definice l-Values naleznete v tématu [výrazy l-value a R-Value](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Viz také

[Souhrn syntaxe jazyka C](../c-language/c-language-syntax-summary.md)<br/>
[Deklarace a typy](../c-language/declarations-and-types.md)<br/>
[Souhrn deklarací](../c-language/summary-of-declarations.md)
