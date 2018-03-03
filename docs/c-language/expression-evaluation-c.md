---
title: "Výraz Evaluation (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9984444bd7de3144cb1e81ddb527c68531a9d7d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluation-c"></a>Vyhodnocení výrazu (C)
Výrazy týkající se přiřazení, unárního zvýšení, unárního snížení nebo volání funkce mohou mít následky související s jejich vyhodnocením (vedlejší účinky). Po dosažení „bodu sekvence“ má vše, co předchází tento bod sekvence, včetně jakýchkoli vedlejších účinků, zaručeno vyhodnocení před zahájením vyhodnocení jakéhokoli následujícího bodu sekvence.  
  
 „Vedlejší účinky“ jsou změny způsobené vyhodnocením výrazu. K vedlejším účinkům dochází, kdykoli se při vyhodnocení výrazu změní hodnota proměnné. Všechny operace přiřazení mají vedlejší účinky. Volání funkce mohou mít také vedlejší účinky, pokud změní hodnotu externě viditelné položky, buď přímým přiřazením, nebo nepřímým přiřazením prostřednictvím ukazatele.  
  
## <a name="see-also"></a>Viz také  
 [Operandy a výrazy](../c-language/operands-and-expressions.md)