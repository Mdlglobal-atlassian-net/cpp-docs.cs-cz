---
title: "Souhrn deklarací | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 53a5e9e5-1a33-40b5-9dea-7f669b479329
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 61dae4cf26f881014f0d98bbf30ebd10a360b10f
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
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
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru* / * pro skalární inicializace     \*/  
  
 *specifikátor třídy úložiště*:  
 **auto**  
  
 **Registrace**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec (**  *extended-decl-modifier-seq*  **)** /* Microsoft Specific \*/  
  
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
  
 *enum-specifier*  
  
 *typedef-name*  
  
 *Kvalifikátor typu*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>opt</sub> *direct-declarator*  
  
 *direct-declarator*:  
 *Identifikátor*  
  
 **(***deklarátor***)**   
  
 *direct-declarator*  **[**  *constant-expression* <sub>opt</sub>**]**  
  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl       \*/  
  
 *deklarátor přímo***(***seznam identifikátorů*<sub>opt</sub>**)** / * deklarátor zastaralé stylu     \*/  
  
 `pointer`:  
 **\*** *type-qualifier-list*<sub>opt</sub>  
  
 **\*** *type-qualifier-list*<sub>opt</sub>`pointer`  
  
 *Seznam parametrů typu*: /\* seznam parametrů \*/  
 *parameter-list*  
  
 *Seznam parametrů* **,...**  
  
 *parameter-list*:  
 *parameter-declaration*  
  
 *Seznam parametrů***,***deklarace parametru*   
  
 *type-qualifier-list*:  
 *type-qualifier*  
  
 *seznam typů kvalifikátor kvalifikátor typu*  
  
 *enum – specifikátor*:  
 **výčet***identifikátor*<sub>opt</sub>**{** *enumerátor seznamu* **}**   
  
 **výčet***identifikátor*   
  
 *Enumerátor seznamu*:  
 *Enumerátor*  
  
 *Enumerátor seznamu***,**   `enumerator`  
  
 `enumerator`:  
 *Konstanta výčtu*  
  
 *Konstanta výčtu***=***konstantní výraz*   
  
 *Konstanta výčtu*:  
 *Identifikátor*  
  
 *struct-or-union-specifier*:  
 *Struktura nebo sjednocení identifikátor*<sub>opt</sub>**{** *seznam struktura prohlášení* **}** *struktura nebo sjednocení identifikátor*  
  
 *Struktura nebo sjednocení*:  
 **struct**  
  
 **sjednocení**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *seznam struktura prohlášení struktura – deklarace*  
  
 *Struktura deklarace*:  
 *specifikátor. kvalifikátor seznamu struktura – deklarátor seznamu***;**   
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list*<sub>opt</sub>  
  
 *Kvalifikátor typu specifikátor kvalifikátor list*<sub>opt</sub>  
  
 *struct-declarator-list*:  
 *Struktura deklarátor struktura – deklarátor seznamu***,***deklarátor – struktura*   
  
 *struct-declarator*:  
 *deklarátor*  
  
 *Specifikátor typu deklarátor*<sub>opt</sub>**:** *konstantní výraz*  
  
 *parameter-declaration*:  
 *specifikátory deklarace deklarátor* / * deklarátor pojmenované \*/  
  
 *specifikátory deklarace abstraktní – deklarátor*<sub>opt</sub>  **/ \***  anonymní deklarátor **\*/**  
  
 *Seznam identifikátorů*:  **/ \***  pro deklarátor starého stylu **\* /**  
 *Identifikátor*  
  
 *Seznam identifikátorů***,***identifikátor*   
  
 *deklarátor abstraktní*:  **/ \***  použít s anonymní deklarátory **\*/**  
 *pointer*  
  
 `pointer`<sub>opt</sub>*direct-abstract-declarator*  
  
 *direct-abstract-declarator*:  
 **(***abstraktní deklarátor***)**   
  
 *direct-abstract-declarator*<sub>opt</sub>**[** *constant-expression*<sub>opt</sub>**]**  
  
 *direct-abstract-declarator*<sub>opt</sub>**(** *parameter-type-list* <sub>opt</sub>**)**  
  
 *Inicializátor*:  
 *assignment-expression*  
  
 **{***inicializátoru seznamu***}** / * pro inicializace agregace     \*/  
  
 **{***inicializátoru seznamu***,}**   
  
 *initializer-list*:  
 *Inicializátor*  
  
 *inicializátoru seznamu***,***inicializátoru*   
  
 *type-name*:  
 *specifier-qualifier-list abstract-declarator*<sub>opt</sub>  
  
 *typedef-name*:  
 *Identifikátor*  
  
 *Rozšířené decl – modifikátor seq*:/\* specifické pro Microsoft \*/  
 *extended-decl-modifier*<sub>opt</sub>  
  
 *extended-decl-modifier-seq extended-decl-modifier*  
  
 *Rozšířené modifikátor decl*: /\* specifické pro Microsoft \*/  
 **thread**  
  
 **naked**  
  
 **dllimport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)   
 [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)   
 [Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)