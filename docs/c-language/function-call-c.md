---
title: Volání funkcí (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: d22bdebc8fa832afb14a2cc09e6a441b7b9e8a5a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233295"
---
# <a name="function-call-c"></a>Volání funkcí (C)

A *volání funkce* je výraz, který obsahuje název volané funkce nebo hodnota ukazatele na funkci a volitelně také argumenty předané funkci.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *výrazu přiřazení*

*Postfix-expression* se musí vyhodnotit na adresu funkce (například identifikátor funkce nebo hodnota ukazatele na funkci), a *argument-expression-list* je seznamem výrazů (oddělených čárkami) jehož hodnoty ("argumenty") jsou předány funkci. *Argument-expression-list* argument může být prázdný.

Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Viz [volání funkce](../c-language/function-calls.md) Další informace.)

## <a name="see-also"></a>Viz také:

[Operátor volání funkce ( )](../cpp/function-call-operator-parens.md)
