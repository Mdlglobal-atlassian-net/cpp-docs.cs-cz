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
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-declarations"></a>Souhrn deklarací
`declaration`:  
 *specifikátory deklarace atribut seq* <sub>opt</sub> *init. deklarátor seznamu*<sub>opt</sub>**;**  
  
 /\**atribut seq* je specifické pro Microsoft * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace*<sub>opt</sub>  
  
 *Specifikátor typu deklarace – specifikátory*<sub>opt</sub>  
  
 *Kvalifikátor typu deklarace – specifikátory*<sub>opt</sub>  
  
 *atribut seq* : /\* *atribut seq* je specifické pro Microsoft\*/  
 *atribut atribut seq* <sub>opt</sub>  
  
 *atribut* : jeden z / * specifické pro Microsoft\*/  
 ||||  
|-|-|-|  
|[__asm](../assembler/inline/asm.md)|[__clrcall](../cpp/clrcall.md)|[__stdcall](../cpp/stdcall.md)|  
|[__based –](../cpp/based-grammar.md)|[__fastcall](../cpp/fastcall.md)|[__thiscall](../cpp/thiscall.md)|  
|[__cdecl](../cpp/cdecl.md)|[__inline](../cpp/inline-functions-cpp.md)|[__vectorcall](../cpp/vectorcall.md)|  
  
 *Init – deklarátor seznamu*:  
 *Init – deklarátor*  
  
 *Init – deklarátor seznamu***,***init deklarátor*   
  
 *Init – deklarátor*:  
 *deklarátor*  
  
 *deklarátor***=***inicializátoru* / * pro skalární inicializace    \*/  
  
 *specifikátor třídy úložiště*:  
 **automaticky**  
  
 **Registrace**  
  
 **static**  
  
 **extern**  
  
 **Definice TypeDef**  
  
 **__declspec (***rozšířené decl – modifikátor seq***)** / * specifické pro Microsoft    \*/  
  
 *Specifikátor typu*:  
 **void**  
  
 **char**  
  
 **short**  
  
 **int**  
  
 `__int8`/ * Konkrétní Microsoft\*/  
  
 `__int16`/ * Konkrétní Microsoft\*/  
  
 `__int32`/ * Konkrétní Microsoft\*/  
  
 `__int64`/ * Konkrétní Microsoft\*/  
  
 **long**  
  
 **float**  
  
 **double**  
  
 **podepsané**  
  
 **bez znaménka**  
  
 *Struktura nebo sjednocení – specifikátor*  
  
 *enum – specifikátor*  
  
 *Název definice TypeDef*  
  
 *Kvalifikátor typu*:  
 **const**  
  
 `volatile`  
  
 `declarator`:  
 `pointer`<sub>OPT</sub> *přímo deklarátor*  
  
 *deklarátor přímo*:  
 *identifikátor*  
  
 **(***deklarátor***)**   
  
 *deklarátor přímo***[***konstantní výraz* <sub>opt</sub>**]**   
  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl      \*/  
  
 *deklarátor přímo***(***seznam identifikátorů*<sub>opt</sub>**)** / * deklarátor zastaralé stylu    \*/  
  
 `pointer`:  
 **\****seznam typů kvalifikátor*<sub>opt</sub>  
  
 **\****seznam typů kvalifikátor*<sub>opt</sub>`pointer`  
  
 *Seznam parametrů typu*: /\* seznam parametrů\*/  
 *Seznam parametrů*  
  
 *Seznam parametrů* **,...**  
  
 *Seznam parametrů*:  
 *deklarace parametru*  
  
 *Seznam parametrů***,***deklarace parametru*   
  
 *seznam typů kvalifikátor*:  
 *Kvalifikátor typu*  
  
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
 *identifikátor*  
  
 *Struktura nebo sjednocení specifikátor*:  
 *Struktura nebo sjednocení identifikátor*<sub>opt</sub>**{** *seznam struktura prohlášení* **}**  *identifikátor struktura nebo sjednocení*  
  
 *Struktura nebo sjednocení*:  
 **struct**  
  
 **sjednocení**  
  
 *seznam struktura prohlášení*:  
 *Struktura – deklarace*  
  
 *seznam struktura prohlášení struktura – deklarace*  
  
 *Struktura deklarace*:  
 *specifikátor. kvalifikátor seznamu struktura – deklarátor seznamu***;**   
  
 *specifikátor. kvalifikátor seznamu*:  
 *Specifikátor typu specifikátor kvalifikátor list*<sub>opt</sub>  
  
 *Kvalifikátor typu specifikátor kvalifikátor list*<sub>opt</sub>  
  
 *Struktura – deklarátor seznamu*:  
 *Struktura deklarátor struktura – deklarátor seznamu***,***deklarátor – struktura*   
  
 *Struktura deklarátor*:  
 *deklarátor*  
  
 *Specifikátor typu deklarátor*<sub>opt</sub>**:** *konstantní výraz*  
  
 *deklarace parametru*:  
 *specifikátory deklarace deklarátor* / * deklarátor pojmenované\*/  
  
 *specifikátory deklarace abstraktní – deklarátor*<sub>opt</sub>  **/ \***  anonymní deklarátor**\*/**  
  
 *Seznam identifikátorů*:  **/ \***  pro deklarátor starého stylu**\* /**  
 *identifikátor*  
  
 *Seznam identifikátorů***,***identifikátor*   
  
 *deklarátor abstraktní*:  **/ \***  použít s anonymní deklarátory**\*/**  
 *ukazatele*  
  
 `pointer`<sub>OPT</sub>*direct abstraktní – deklarátor*  
  
 *Direct abstraktní – deklarátor*:  
 **(***abstraktní deklarátor***)**   
  
 *Direct abstraktní – deklarátor*<sub>opt</sub>**[** *konstantní výraz*<sub>opt</sub>**]**  
  
 *Direct abstraktní – deklarátor*<sub>opt</sub>**(** *seznam parametrů typu* <sub>opt</sub>**)**  
  
 *Inicializátor*:  
 *přiřazení – výraz*  
  
 **{***inicializátoru seznamu***}** / * pro inicializace agregace    \*/  
  
 **{***inicializátoru seznamu***,}**   
  
 *inicializátoru seznamu*:  
 *Inicializátor*  
  
 *inicializátoru seznamu***,***inicializátoru*   
  
 *Název typu*:  
 *specifikátor. kvalifikátor seznamu abstraktní – deklarátor*<sub>opt</sub>  
  
 *TypeDef – název*:  
 *identifikátor*  
  
 *Rozšířené decl – modifikátor seq*:/\* specifické pro Microsoft\*/  
 *Rozšířené modifikátor decl*<sub>opt</sub>  
  
 *Rozšířené rozšířené decl – modifikátor seq – decl – modifikátor*  
  
 *Rozšířené modifikátor decl*: /\* specifické pro Microsoft\*/  
 **thread**  
  
 **holé**  
  
 **DllImport**  
  
 `dllexport`  
  
## <a name="see-also"></a>Viz také  
 [Konvence volání](../cpp/calling-conventions.md)   
 [Gramatika struktury fráze](../c-language/phrase-structure-grammar.md)   
 [Zastaralé konvence volání](../cpp/obsolete-calling-conventions.md)