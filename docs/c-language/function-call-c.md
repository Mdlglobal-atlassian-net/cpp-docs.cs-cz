---
title: Funkce Call (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ec4e92774cdec75e47c07407ee72444a7486f7f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43751332"
---
# <a name="function-call-c"></a>Volání funkcí (C)

A *volání funkce* je výraz, který obsahuje název volané funkce nebo hodnota ukazatele na funkci a volitelně také argumenty předané funkci.  
  
## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***(***argument-expression-list*<sub>optimalizované</sub> **)**   
  
*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přiřazení*<br/> &nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *výrazu přiřazení*  
  
*Postfix-expression* se musí vyhodnotit na adresu funkce (například identifikátor funkce nebo hodnota ukazatele na funkci), a *argument-expression-list* je seznamem výrazů (oddělených čárkami) jehož hodnoty ("argumenty") jsou předány funkci. *Argument-expression-list* argument může být prázdný.  
  
Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Viz [volání funkce](../c-language/function-calls.md) Další informace.)  
  
## <a name="see-also"></a>Viz také

[Operátor volání funkce ( )](../cpp/function-call-operator-parens.md)