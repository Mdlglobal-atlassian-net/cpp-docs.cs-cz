---
title: Souhrn deklarací
ms.date: 11/04/2016
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
ms.openlocfilehash: e553f4bdfffcd4bba6a39b2d37af6ba25a3d65d9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170433"
---
# <a name="summary-of-declarations"></a>Souhrn deklarací

*deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – atribut specifikátors* *-SEQ*<sub>opt</sub> *init-deklarátor-list*<sub>opt</sub> **;**

*specifikátory deklarace*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru třídy úložiště* – *specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarace *specifikátoru typu* *– Povolit specifikátory*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ-specifikátor deklarace kvalifikátoru* *– specifikátory*<sub>opt</sub>

*atribut-seq* &nbsp; &nbsp; &nbsp; &nbsp; :/ specifické pro společnost Microsoft\*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*attribute* *atribut atributu-SEQ*<sub>opt</sub>

*atribut* : jeden z&nbsp; &nbsp; &nbsp; &nbsp; / \* specifických pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;[__asm](../assembler/inline/asm.md) [__clrcall](../cpp/clrcall.md) [__stdcall](../cpp/stdcall.md) [__based](../cpp/based-grammar.md) [__fastcall](../cpp/fastcall.md) [__thiscall](../cpp/thiscall.md) [__cdecl](../cpp/cdecl.md) [__inline](../cpp/inline-functions-cpp.md) [__vectorcall](../cpp/vectorcall.md)

*init-deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarátor-list*  **,**  *init-deklarátor*

*init-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor***=** / *initializer* inicializátor\* pro skalární inicializaci    \*/

*specifikátor třídy úložiště*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**automaticky**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Registrace**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**tras**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**definic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (** *Rozšířené prohlášení-modifikátor-SEQ* **)**  / \* specifické pro společnost Microsoft\*/

*specifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**šekem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**char**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dostatečná**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**hmot**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int8** / __int8\* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int16** / __int16\* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int32** / __int32\* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__int64** / __int64\* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dlouhou**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Plovák**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**klepat**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**podpisy**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**celé**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor struct nebo Union*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enum – specifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typedef – název*

*kvalifikátor typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**MX**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**permanentní**

*deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel na odkaz*<sub>opt</sub> *Direct – deklarátor*

*přímý – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **[** opt *-Expression*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **(** *parametr-Type-list* **)**  / \* – nový styl deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-deklarátor* **(opt** *-list*<sub>opt</sub> **)**  / \* zastaralý styl deklarátor\*/

*ukazatel*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*kvalifikátor typu – seznam –*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;<strong>\*</strong>*Type-kvalifikátor – ukazatel na seznam*<sub>výslovných</sub> *pointer*

*seznam parametrů-typu*&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; :&nbsp; &nbsp; &nbsp; &nbsp; seznam&nbsp; &nbsp; &nbsp; / \*\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam parametrů* **,...**

*seznam parametrů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametr-list* **,** *parametr-Declaration*

*typ – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*kvalifikátor typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;kvalifikátor typu – *kvalifikátor typu* *seznamu*

*specifikátor výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;<sub>výslovný souhlas</sub> s *identifikátorem* **výčtu** **{** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**enum** *identifikátor* výčtu

*seznam enumerátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*čítače*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*enumerátor – seznam* **,** *enumerátor*

*enumerátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výčet – konstanta*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Enumeration –* **=** konstantní *výraz*

*konstanta výčtu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*

*specifikátor struct nebo Union*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor ID* *struktury nebo sjednocení* –<sub>opt</sub> **{** *struct-Declaration-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor* *struktury nebo sjednocení*

*Struktura nebo sjednocení*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nemají**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**sjednocovací**

*Struktura-deklarace-seznamu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*struct – deklarace*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura-deklarace-seznamu* *Struktura-deklarace*

*deklarace struktury*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor-kvalifikátor-list* *struct-deklarátor-list* **;**

*specifikátor – kvalifikátor – seznam*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *specifikátoru typu* *– kvalifikátor – seznam*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;specifikátor *kvalifikátoru typu* – *Kvalifikátor seznamu – kvalifikátor*<sub>opt</sub>

*Struktura – deklarátor-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Struktura-deklarátor* *Struktura-deklarátor-list* **,** *struct-deklarátor*

*Struktura – deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*typ – specifikátor* *deklarátor*<sub>opt</sub> **:** *konstantní výraz*

*deklarace parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *deklarátor*  / \* s názvem deklarátor\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory* *abstract-deklarátor*<sub>opt</sub>  / \* anonymní deklarátor\*/

*seznam identifikátorů*:/\* pro deklarátor starého stylu\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*seznam identifikátorů* **,** *identifikátor*

*abstract-deklarátor*:/\* používá se anonymním deklarátory\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatele*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ukazatel*<sub>opt</sub> *Direct – abstract-deklarátor*

*Direct-abstract-deklarátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**(** *abstract-deklarátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-abstract-deklarátor*<sub>opt</sub> **[** *výrazová odpověď konstanty*<sub>opt</sub> **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Direct-abstract-deklarátor*<sub>opt</sub> **(** *parametr-Type-list-*<sub>opt</sub> **)**

*inicializátor*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *inicializátor-list* **}**  / \* pro inicializaci agregace\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *inicializátor-list* **,}**

*seznam inicializátorů*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*inicializátor – seznam* **,** *inicializátor*

*název typu*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátor – kvalifikátor – seznam* *Abstrakt-deklarátor –*<sub>výslovný souhlas</sub>

*definice typedef-Name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*RID*

*Extended---modifikátor-SEQ*:&nbsp; &nbsp; &nbsp; &nbsp; / \* specifické pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Rozšířené-prohlášení – modifikátor*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended---modifikátor-SEQ* *Extended---modifikátor*

*Rozšířené – modifikátor*&nbsp; &nbsp; &nbsp; &nbsp; :/ specifické\* pro společnost Microsoft\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Doporučujeme**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**okem**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**atributu**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**

## <a name="see-also"></a>Viz také

[Konvence volání](../cpp/calling-conventions.md)<br/>
[Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)<br/>
[Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)
