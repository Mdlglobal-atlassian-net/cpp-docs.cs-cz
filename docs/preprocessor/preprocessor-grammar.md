---
title: Gramatika preprocesoru
ms.date: 08/29/2019
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: f0916e3cc9bbdb398db693286dacc4517df03557
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222257"
---
# <a name="preprocessor-grammar"></a>Gramatika preprocesoru

*řídicí čára*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identifikátor* *token – řetězec* <sub>výslovný souhlas</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *identifikátor* **(** &#x2800;&#x200B;<sub>souhlas</sub> **s** identifikátorem,... **,** *identifikátor* &#x200B; <sub></sub>opt&#x2800; **)** *token – opt-String*<sub></sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _cesta – specifikace_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** _cesta – specifikace_ **\<** **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *sekvence číslic* **"** _název souboru_ **"** &#x200B; <sub>výslovný souhlas</sub>  \
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *token – řetězec*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token – řetězec*

*konstantní výraz*: \
&nbsp;&nbsp;&nbsp;&nbsp;**definováno (** &#x2800;*identifikátor*&#x2800; **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**definováno** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp;jakýkoli jiný konstantní výraz

*podmíněné*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if – část* *elif – části* <sub>výslovný souhlas</sub> *Else – část* <sub>výslovný souhlas</sub> *endif-line*

*if-Part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-line* *text*

*řádek if-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *konstantní výraz*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *identifikátor*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifikátor*

*elif – části*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif-line* *text*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif – části* *elif-line* *text*

*elif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *konstantní výraz*

*Else – část*: \
&nbsp;&nbsp;&nbsp;&nbsp;*Else-line* *text*

*Else-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-line*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*sekvence číslic*: \
&nbsp;&nbsp;&nbsp;&nbsp;*základní*\
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *číslice*

*číslice*: jedna z těchto \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*řetězec tokenu*: \
&nbsp;&nbsp;&nbsp;&nbsp;Řetězec tokenů

*token*: \
&nbsp;&nbsp;&nbsp;&nbsp;*klíčové slovo*\
&nbsp;&nbsp;&nbsp;&nbsp;*RID*\
&nbsp;&nbsp;&nbsp;&nbsp;*změnil*\
&nbsp;&nbsp;&nbsp;&nbsp;*podnikatel*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*název souboru*: \
&nbsp;&nbsp;&nbsp;&nbsp;Platný název souboru operačního systému

*cesta-specifikace*: \
&nbsp;&nbsp;&nbsp;&nbsp;Platná cesta k souboru

*text*: \
&nbsp;&nbsp;&nbsp;&nbsp;Libovolná sekvence textu

> [!NOTE]
> Následující neterminály se rozbalí v části [lexikální konvence](../cpp/lexical-conventions.md) referenčního  *C++ jazyka*: konstanta, *konstantní výraz*, *identifikátor*, *klíčové slovo*, *operátor*a.  *punctuator*.

## <a name="see-also"></a>Viz také:

[Souhrn gramatiky (CC++/)](../preprocessor/grammar-summary-c-cpp.md)
