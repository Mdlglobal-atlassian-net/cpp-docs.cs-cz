---
title: Tělo funkce
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 2d2e04572de91b161237d999bb95cfda26256c54
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857096"
---
# <a name="function-body"></a>Tělo funkce

*Tělo funkce* je složený příkaz obsahující příkazy, které určují, co funkce dělá.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarace – specifikátory*<sub>opt</sub> *atribut – seq*<sub>opt</sub> *deklarátor* *deklarace-list*<sub>opt</sub> – *složený* příkaz

/\**atribut – seq* je specifický pro společnost Microsoft\*/

*složený*příkaz:/\* tělo funkce\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklarace-seznam*příkazů<sub>opt</sub> *-list*<sub>opt</sub> **}**

Proměnné deklarované v těle funkce, označované jako *místní proměnné*, mají **auto** třídy úložiště, pokud není uvedeno jinak. Při volání funkce se vytvoří úložiště pro místní proměnné a provede se místní inicializace. Řízení spouštění předává prvnímu příkazu v *složeném výrazu* a pokračuje, dokud není proveden **návratový** příkaz nebo dokud se nenajde konec textu funkce. Ovládací prvek se pak vrátí do bodu, ve kterém byla funkce volána.

Příkaz **return** obsahující výraz musí být proveden, pokud funkce vrátí hodnotu. Návratová hodnota funkce není definována, pokud není proveden žádný **návratový** příkaz nebo pokud příkaz **return** nezahrnuje výraz.

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)
