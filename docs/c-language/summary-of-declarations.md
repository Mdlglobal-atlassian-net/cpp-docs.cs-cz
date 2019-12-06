---
title: Souhrn deklarací
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: 88cfc78089e0efd4765a40ab0d9c6dc333deb125
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857018"
---
# <a name="summary-of-declarations"></a>Souhrn deklarací

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;atribut *deklarace-specifikátor* *-SEQ*<sub>opt</sub> *-deklarátor-list*<sub>opt</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*třídy úložiště* -specifikátory *deklarace specifikátor-* <sub></sub> specifikátory<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *specifikátoru typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory*<sub></sub> *kvalifikátoru typu* -deklarace

*atribut-seq* :&nbsp;&nbsp;&nbsp;&nbsp;/\* \*specifických pro společnost Microsoft /<br/>
&nbsp;&nbsp;&nbsp;atributu *atributu* &nbsp; *– SEQ*<sub>opt</sub>

*atribut* : jedna z&nbsp;&nbsp;&nbsp;&nbsp;/\* \*pro konkrétní Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Init-declarator-list* **,** *init-declarator*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor* **=** *inicializátor*  / \* pro skalární inicializace \*/

*specifikátor třídy úložiště*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**auto**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**registraci**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;**definice** typu &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Rozšířený--modifikátor-SEQ* **)**  /\* \*specifický pro společnost Microsoft /

*specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**void**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**znak**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**short**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**int**<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int8** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int16** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int32** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__int64** /\* \*/ pro konkrétní Microsoft<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Long**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**float**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Double**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podepsané**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**bez znaménka**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-or-Union-specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor enum*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef-Name*

*kvalifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**const**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**volatile**

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatelem*<sub>opt</sub> *Direct-deklarátor*

*přímý – deklarátor*:<br/>
*identifikátor* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **[** opt *-Expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct deklarátor* **(** *parametr-Type-list* **)**  /\* nového stylu deklarátor \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **(** opt *-list*<sub>opt</sub> **)**  /\* zastaralý styl deklarátor \*/

*pointer*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *kvalifikátor typu – zobrazit*<sub>výslovný souhlas</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong> *kvalifikátor typu – ukazatel na seznam*<sub>opt</sub>

*parametr-Type-list*:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;/\* seznamu parametrů \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,** *Parameter-Declaration*

*typ – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kvalifikátor typu*<br/>
&nbsp;&nbsp;&nbsp;*typ &nbsp;kvalifikátor –* *kvalifikátor typu* seznamu

*specifikátor výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**identifikátor výčtu**<sub>opt</sub> **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;identifikátor **výčtu** &nbsp;

*seznam enumerátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerátor-list* **,** *enumerátor*

*enumerátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výčtu – konstanta*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanta výčtu* **=** *konstantního výrazu.*

*konstanta výčtu*:<br/>
*identifikátor* &nbsp;&nbsp;&nbsp;&nbsp;

*specifikátor struct nebo Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; *-li identifikátor sjednocení nebo identifikátor sjednocení*<sub></sub> **{** *struct-Declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;*identifikátoru* *struktury &nbsp;nebo Union*

*Struktura nebo sjednocení*:<br/>
&nbsp;&nbsp;&nbsp;**struktura** &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Union**

*Struktura-deklarace-seznamu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-Declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-Declaration-list* *– deklarace*

*deklarace struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor-kvalifikátor-list* *struct-deklarátor-list* **;**

*specifier-qualifier-list*:<br/>
&nbsp;&nbsp;&nbsp;specifikátoru *specifikátoru typu* &nbsp;– *kvalifikátor – seznam*<sub></sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *kvalifikátoru typu* – *kvalifikátor – seznam*<sub></sub>

*struct-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct-deklarátor* *struct-deklarátor-list* **,** *struct-deklarátor*

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor typu* *deklarátor*<sub>opt</sub> **:** *konstantní výraz*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory* *deklarátor* /\* s názvem deklarátor \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace* *abstract-deklarátor*<sub>opt</sub> /\* anonymní deklarátor \*/

*seznam identifikátorů*:/\* pro původní styl deklarátor \*/<br/>
*identifikátor* &nbsp;&nbsp;&nbsp;&nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor-seznam* **,** *identifikátor*

*abstract-deklarátor*:/\* používá se anonymní deklarátory \*/<br/>
&nbsp;&nbsp;&nbsp;*ukazatel* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-abstract-declarator*

*direct-abstract-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **(** *abstract-deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-abstract-declarator*<sub>opt</sub> **[** *constant-expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-abstract-deklarátor*<sub>opt</sub> **(** možnost<sub>opt</sub> - *Type-list* **)**

*inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicializátor-list* **}**  /\* pro agregovanou inicializaci \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **{** *inicializátor-list* **,}**

*seznam inicializátorů*:<br/>
&nbsp;&nbsp;&nbsp;*inicializátor* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializátor-list* **,** *inicializátor*

*název typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor-kvalifikátor-list* - *deklarátor*–<sub>výslovný souhlas</sub>

*definice typedef-Name*:<br/>
*identifikátor* &nbsp;&nbsp;&nbsp;&nbsp;

Rozšířený-&nbsp;– *Modifikátor-SEQ*: &nbsp;&nbsp;&nbsp;/\* \*specifické pro společnost Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier-seq* *extended-decl-modifier*

*Rozšířené – modifikátor*:&nbsp;&nbsp;&nbsp;&nbsp;/\* \*pro konkrétní Microsoft /<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**vlákno**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**holé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Viz také:

[Konvence volání](../cpp/calling-conventions.md)<br/>
[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)<br/>
[Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)