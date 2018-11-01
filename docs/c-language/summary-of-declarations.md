---
title: Souhrn deklarací
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: 21d6866f8e0b370d8a0d93253a6259302666963a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647197"
---
# <a name="summary-of-declarations"></a>Souhrn deklarací

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *sekvence atributů*<sub>optimalizované</sub> *init-declarator-list*<sub>optimalizované</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátory deklarace*<sub>optimalizované</sub>

*sekvence atributů* :&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atribut* *sekvence atributů*<sub>optimalizované</sub>

*atribut* : jeden z&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [klíčové slovo __thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list***,***init-declarator*

*Init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor***=***inicializátor*  / \* pro skalární inicializace \*/

*Storage-class-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Automaticky**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Registrace**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Statická**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Definice TypeDef**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *extended-decl-modifier-seq* **)**  / \* specifické pro Microsoft \*/

*Specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Typ void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**krátké**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64**  / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**plovoucí desetinnou čárkou**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podepsané**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaménka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct – nebo – sjednocení – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enum – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Název TypeDef*

*Kvalifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Volatile**

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>optimalizované</sub> *direct-declarator*

*přímé declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **[** *konstantní výraz*<sub>optimalizované</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam parametrů typu* **)**  / \* deklarátor nový styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé declarator* **(** *seznam identifikátorů*<sub>optimalizované</sub> **)**  / \* Obsolete – vizuální styl deklarátor \*/

*ukazatel*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *seznam typů kvalifikátor*<sub>optimalizované</sub> *ukazatele*

*Seznam parametrů typu*:&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; / \* Seznam parametrů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,...**

*Seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam parametrů* **,** *deklarace parametru*

*seznam typů kvalifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam typů kvalifikátor* *kvalifikátor typu*

*specifikátoru výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**výčet** *identifikátor*<sub>optimalizované</sub> **{** *enumerátor seznam* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**výčet** *identifikátor*

*Enumerátor seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumerátor seznam* **,** *enumerátoru*

*enumerátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu* **=** *konstantního výrazu.*

*Konstanta výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

*struct – nebo – sjednocení specifikátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura nebo sjednocení* *identifikátor*<sub>optimalizované</sub> **{** *struct-declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura nebo sjednocení* *identifikátor*

*Struktura nebo sjednocení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**– Struktura**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sjednocení**

*struct-declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace struktury*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-declaration-list* *struct-declaration*

*struct-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor qualifier-list* *struct-declarator-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kvalifikátor typu* *specifikátor seznam kvalifikátorů-*<sub>optimalizované</sub>

*Struktura declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura declarator* *struct-declarator-list* **,** *deklarátor – struktura*

*Struktura declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specifikátor typu* *deklarátor*<sub>optimalizované</sub> **:** *konstantního výrazu.*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *deklarátor*  / \* pojmenované deklarátorů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstraktní deklarátor*<sub>optimalizované</sub>  / \* anonymní deklarátorů \*/

*Seznam identifikátorů*: /\* pro deklarátor starého stylu \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Seznam identifikátorů* **,** *identifikátor*

*abstraktní deklarátor*: /\* použít s anonymní deklarátorů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Ukazatel*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>optimalizované</sub> *direct abstraktní declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *abstraktní deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé abstraktní declarator*<sub>optimalizované</sub> **[** *konstantní výraz*<sub>optimalizované</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*přímé abstraktní declarator*<sub>optimalizované</sub> **(** *seznam parametrů typu*<sub>optimalizované</sub> **)**

*Inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam inicializátorů* **}**  / \* pro inicializace agregace \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam inicializátorů* **,}**

*seznam inicializátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Inicializátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam inicializátorů* **,** *inicializátor*

*Název typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor qualifier-list* *abstraktní deklarátor*<sub>optimalizované</sub>

*Název typedef*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*

*Extended-decl-modifier-seq*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl modifikátor*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-modifier-seq* *extended-decl – modifikátor*

*Extended-decl modifikátor*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro Microsoft \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**DllImport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)<br/>
[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)<br/>
[Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)