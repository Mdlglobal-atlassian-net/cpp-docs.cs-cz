---
title: Funkce text | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d30cb5429ebee0738aa7b7aab367d79867e92047
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757816"
---
# <a name="function-body"></a>Tělo funkce

A *tělo funkce* je složeného příkazu, který obsahuje příkazy, které určují, co funkce dělá.

## <a name="syntax"></a>Syntaxe

*definice funkce*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specifikátory deklarace*<sub>optimalizované</sub> *sekvence atributů*<sub>optimalizované</sub> *deklarátor* *seznam deklarací*  <sub>optimalizované</sub> *compound-statement*

/\* *sekvence atributů* je specifické pro Microsoft \*/

*compound-statement*: /\* tělo funkce \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *seznam deklarací*<sub>optimalizované</sub> *seznamu příkazů*<sub>optimalizované</sub> **}**

Proměnné deklarované v těle funkce, označované jako *lokální proměnné*, mají **automaticky** třída úložiště není uvedeno jinak. Při volání funkce úložiště se vytvoří pro místní proměnné a jsou prováděny místní inicializace. První příkaz v předá řízení provádění *compound-statement* a pokračuje až do **vrátit** je proveden příkaz nebo konec tělo funkce nebude nalezen. Ovládací prvek vrátí do bodu, ve kterém byla volána funkce.

A **vrátit** příkazu, který obsahuje výraz musí být provedeny, pokud je funkce vrátit hodnotu. Návratové hodnoty funkce není definováno, pokud žádné **vrátit** je proveden příkaz nebo, pokud **vrátit** příkaz neobsahuje výraz.

## <a name="see-also"></a>Viz také

[Definice funkcí jazyka C](../c-language/c-function-definitions.md)