---
title: Gramatika preprocesoru
ms.date: 09/04/2018
helpviewer_keywords:
- preprocessor
- grammar, preprocessor
- preprocessor, grammar
ms.assetid: 6cd33fad-0b08-4592-9be8-7359c43e24e9
ms.openlocfilehash: 17768b7ec1442f2af1abf76596527d4df69b1534
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614185"
---
# <a name="preprocessor-grammar"></a>Gramatika preprocesoru

*ovládací prvek řádku*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** *identifikátor* *řetězci tokenu*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#define** <em>identifikátor</em>**(** *identifikátor*<sub>optimalizované</sub> **,** ... **,** *identifikátor*<sub>optimalizované</sub> **)** *řetězci tokenu*<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **"** *path-spec* **"**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#include** **\<** *path-spec* **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#line** *sekvence číslic***"** *filename* **"**<sub>optimalizované</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#undef** *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#error** *řetězci tokenu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#pragma** *řetězci tokenu*

*konstantní výraz*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**definovaný (** *identifikátor* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**definované** *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Další konstantní výraz

*Podmíněné* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*část IF* *části elif*<sub>optimalizované</sub> *část else*<sub>optimalizované</sub> *řádek endif*

*část IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řádek IF* *text*

*řádek IF* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if** *konstantního výrazu.*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef** *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef** *identifikátor*

*části elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řádek elif* *text*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*části elif* *řádku elif* *text*

*řádek elif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif** *konstantního výrazu.*

*části else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*řádek else* *text*

*řádek else* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*řádek endif* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

*sekvence číslic* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*číslice*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*sekvence číslic* *číslice*

*číslice* : jeden z<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*řetězcový token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Řetězec tokenů

*token* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Klíčové slovo*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Konstanty*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*– Operátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*interpunkci*

*Název souboru* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Název souboru právní operačního systému

*Path-spec* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Cesta k souboru právní

*text* :<br/>
&nbsp;&nbsp;&nbsp;&nbsp;Libovolná sekvence textu

> [!NOTE]
> Následující neterminály jsou rozbaleny v [lexikální konvence](../cpp/lexical-conventions.md) část *referenční dokumentace jazyka C++*: *konstantní*, *konstantního výrazu.* , *identifikátor*, *– klíčové slovo*, *operátor*, a *interpunkci*.

## <a name="see-also"></a>Viz také

[Gramatický souhrn (C/C++)](../preprocessor/grammar-summary-c-cpp.md)