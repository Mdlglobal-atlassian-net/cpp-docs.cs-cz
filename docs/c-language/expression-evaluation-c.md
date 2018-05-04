---
title: Výraz Evaluation (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9c250cba9e26d82ba129a842b61006783d13f6e3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="expression-evaluation-c"></a>Vyhodnocení výrazu (C)
Výrazy týkající se přiřazení, unárního zvýšení, unárního snížení nebo volání funkce mohou mít následky související s jejich vyhodnocením (vedlejší účinky). Po dosažení „bodu sekvence“ má vše, co předchází tento bod sekvence, včetně jakýchkoli vedlejších účinků, zaručeno vyhodnocení před zahájením vyhodnocení jakéhokoli následujícího bodu sekvence.  
  
 „Vedlejší účinky“ jsou změny způsobené vyhodnocením výrazu. K vedlejším účinkům dochází, kdykoli se při vyhodnocení výrazu změní hodnota proměnné. Všechny operace přiřazení mají vedlejší účinky. Volání funkce mohou mít také vedlejší účinky, pokud změní hodnotu externě viditelné položky, buď přímým přiřazením, nebo nepřímým přiřazením prostřednictvím ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [Operandy a výrazy](../c-language/operands-and-expressions.md)