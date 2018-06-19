---
title: Souhrn deklarací | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9e5fe380d41b5d1e58a63b1aa0b99a239dee515
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32392520"
---
# <a name="summary-of-declarations"></a>Souhrn deklarací
`declaration`:  
 *specifikátory deklarace atribut seq* <sub>opt</sub> *init. deklarátor seznamu*<sub>opt</sub>**;**  
  
 /\* *atribut seq* je specifické pro Microsoft * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace*<sub>opt</sub>  
  
 *Specifikátor typu deklarace – specifikátory*<sub>opt</sub>  
  
 *Kvalifikátor typu deklarace – specifikátory*<sub>opt</sub>  
  
 *atribut seq* : /\* *atribut seq* je specifické pro Microsoft \*/  
 *atribut atribut seq* <sub>opt</sub>  
  
 *atribut* : jeden z / * specifické pro Microsoft \*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *Init – deklarátor seznamu***,***init deklarátor*   
  
 *Init – deklarátor*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru* / * pro skalární inicializace \*/  
  
 *specifikátor třídy úložiště*:  
 **auto**  
  
 **Registrace**  
  
 **static**  
  
 **extern**  
  
 **Definice TypeDef**  
  
 **__declspec (***rozšířené decl – modifikátor seq***)** / * specifické pro Microsoft     \*/  
  
 *Specifikátor typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8` / * Konkrétní Microsoft \*/  
  
 `__int16` / * Konkrétní Microsoft \*/  
  
 `__int32` / * Konkrétní Microsoft \*/  
  
 `__int64` / * Konkrétní Microsoft \*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **Podepsané**  
  
 **Bez znaménka**  
  
 *struct-or-union-specifier*  
  
 *enum – specifikátor*  
  
 *typedef-name*  
  
 *Kvalifikátor typu*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>OPT</sub> *přímo deklarátor*  
  
 *deklarátor přímo*:  
 *Identifikátor*  
  
 **(***deklarátor***)**  
  
 *deklarátor přímo***[***konstantní výraz* <sub>opt</sub>**]**   
  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl \*/  
  
 *deklarátor přímo***(***seznam identifikátorů*<sub>opt</sub>**)** / * deklarátor zastaralé stylu \*/  
  
 `pointer`:  
 **\*** *seznam typů kvalifikátor*<sub>opt</sub>  
  
 **\*** *seznam typů kvalifikátor*<sub>opt</sub>`pointer`  
  
 *Seznam parametrů typu*: /\* seznam parametrů \*/  
 *parameter-list*  
  
 *Seznam parametrů* **,...**  
  
 *Seznam parametrů*:  
 *parameter-declaration*  
  
 *Seznam parametrů***,***deklarace parametru*  
  
 *seznam typů kvalifikátor*:  
 *Kvalifikátor typu*  
  
 *seznam typů kvalifikátor kvalifikátor typu*  
  
 *enum – specifikátor*:  
 **výčet***identifikátor*<sub>opt</sub>**{** *enumerátor seznamu* **}**  
  
 **výčet***identifikátor*  
  
 *Enumerátor seznamu*:  
 *Enumerátor*  
  
 *Enumerátor seznamu***,**  `enumerator`  
  
 `enumerator`:  
 *Konstanta výčtu*  
  
 *Konstanta výčtu***=***konstantní výraz*  
  
 *Konstanta výčtu*:  
 *Identifikátor*  
  
 *Struktura nebo sjednocení specifikátor*:  
 *Struktura nebo sjednocení identifikátor*<sub>opt</sub>**{** *seznam struktura prohlášení* **}** *struktura nebo sjednocení identifikátor*  
  
 *Struktura nebo sjednocení*:  
 **struct**  
  
 **sjednocení**  
  
 *seznam struktura prohlášení*:  
 *Struktura – deklarace*  
  
 *seznam struktura prohlášení struktura – deklarace*  
  
 *Struktura deklarace*:  
 *specifikátor. kvalifikátor seznamu struktura – deklarátor seznamu***;**  
  
 *specifier-qualifier-list*:  
 *Specifikátor typu specifikátor kvalifikátor list*<sub>opt</sub>  
  
 *Kvalifikátor typu specifikátor kvalifikátor list*<sub>opt</sub>  
  
 *Struktura – deklarátor seznamu*:  
 *Struktura deklarátor struktura – deklarátor seznamu***,***deklarátor – struktura*  
  
 *Struktura deklarátor*:  
 *deklarátor*  
  
 *Specifikátor typu deklarátor*<sub>opt</sub>**:** *konstantní výraz*  
  
 *deklarace parametru*:  
 *specifikátory deklarace deklarátor* / * deklarátor pojmenované \*/  
  
 *specifikátory deklarace abstraktní – deklarátor*<sub>opt</sub> **/ \*** anonymní deklarátor **\*/**  
  
 *Seznam identifikátorů*: **/ \*** pro deklarátor starého stylu **\* /**  
 *Identifikátor*  
  
 *Seznam identifikátorů***,***identifikátor*  
  
 *deklarátor abstraktní*: **/ \*** použít s anonymní deklarátory **\*/**  
 *Ukazatele*  
  
 `pointer`<sub>opt</sub>*direct-abstract-declarator*  
  
 *direct-abstract-declarator*:  
 **(***abstraktní deklarátor***)**  
  
 *direct-abstract-declarator*<sub>opt</sub>**[** *constant-expression*<sub>opt</sub>**]**  
  
 *direct-abstract-declarator*<sub>opt</sub>**(** *parameter-type-list* <sub>opt</sub>**)**  
  
 *Inicializátor*:  
 *assignment-expression*  
  
 **{***inicializátoru seznamu***}** / * pro inicializace agregace \*/  
  
 **{***inicializátoru seznamu***,}**  
  
 *inicializátoru seznamu*:  
 *Inicializátor*  
  
 *inicializátoru seznamu***,***inicializátoru*  
  
 *Název typu*:  
 *specifikátor. kvalifikátor seznamu abstraktní – deklarátor*<sub>opt</sub>  
  
 *TypeDef – název*:  
 *Identifikátor*  
  
 *Rozšířené decl – modifikátor seq*:/\* specifické pro Microsoft \*/  
 *extended-decl-modifier*<sub>opt</sub>  
  
 *Rozšířené rozšířené decl – modifikátor seq – decl – modifikátor*  
  
 *Rozšířené modifikátor decl*: /\* specifické pro Microsoft \*/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)   
 [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)   
 [Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)