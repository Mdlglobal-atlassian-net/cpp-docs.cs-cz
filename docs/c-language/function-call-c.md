---
title: Funkce Call (C) | Microsoft Docs
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
ms.openlocfilehash: 49c9483cb6e556d5a8b174377c0dad666834c9e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="function-call-c"></a>Volání funkcí (C)
„Volání funkce“ je výraz, který obsahuje název volané funkce nebo hodnotu ukazatele na funkci a volitelně také argumenty funkci předané.  
  
## <a name="syntax"></a>Syntaxe  
 *operátory výraz*:  
 *operátory výraz***(***seznam argumentů výraz* opt **)**   
  
 *Seznam argumentů výraz*:  
 *assignment-expression*  
  
 *Seznam argumentů výraz***,***přiřazení – výraz*   
  
 *Operátory výraz* adresu funkce (například identifikátor funkce nebo hodnota ukazatel na funkci), se musí vyhodnotit a *seznam argumentů výraz* je seznam výrazů (oddělené čárkami) jejichž hodnoty ("argumenty") jsou předaný funkci. *Seznam argumentů výraz* argument nesmí být prázdné.  
  
 Výraz volání funkce má hodnotu a typ návratové hodnoty funkce. Funkce nemůže vracet objekt typu pole. Je-li návratovým typem funkce typ `void` (tedy funkce byla deklarována tak, aby nikdy nevracela hodnotu), je výraz volání funkce také typu `void`. (Viz [volání funkce](../c-language/function-calls.md) Další informace.)  
  
## <a name="see-also"></a>Viz také  
 [Operátor volání funkce ( )](../cpp/function-call-operator-parens.md)