---
title: Volání funkcí (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: 46e010ed625e23aa6c21b8c78280b714c68582b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50478114"
---
# <a name="function-call-c"></a>Volání funkcí (C)

A *volání funkce* je výraz, který obsahuje název volané funkce nebo hodnota ukazatele na funkci a volitelně také argumenty předané funkci.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *výrazu přiřazení*

*Postfix-expression* se musí vyhodnotit na adresu funkce (například identifikátor funkce nebo hodnota ukazatele na funkci), a *argument-expression-list* je seznamem výrazů (oddělených čárkami) jehož hodnoty ("argumenty") jsou předány funkci. *Argument-expression-list* argument může být prázdný.

Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Viz [volání funkce](../c-language/function-calls.md) Další informace.)

## <a name="see-also"></a>Viz také

[Operátor volání funkce ( )](../cpp/function-call-operator-parens.md)