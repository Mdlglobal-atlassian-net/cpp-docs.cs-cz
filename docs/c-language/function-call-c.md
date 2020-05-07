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

*Volání funkce* je výraz, který obsahuje název funkce, která je volána nebo hodnota ukazatele na funkci, a volitelně argumenty předávané funkci.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *přiřazení-výraz*

*Výraz přípony* musí být vyhodnocen jako adresa funkce (například identifikátor funkce nebo hodnota ukazatele na funkci) a *argument-expression-list* je seznam výrazů (oddělených čárkami), jejichž hodnoty ("argumenty") jsou předány funkci. Argument *-Expression-list* může být prázdný.

Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Další informace naleznete v tématu [volání funkcí](../c-language/function-calls.md) .)

## <a name="see-also"></a>Viz také

[Operátor volání funkce: ()](../cpp/function-call-operator-parens.md)
