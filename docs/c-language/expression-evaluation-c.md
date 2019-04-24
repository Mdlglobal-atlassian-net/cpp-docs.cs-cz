---
title: Vyhodnocení výrazu (C)
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation
- expressions [C++], evaluating
ms.assetid: 9493f8cc-64a2-4284-9aaf-26eec11c4f40
ms.openlocfilehash: 37affedc0bcf3fb1423898ecf2c570794d9625c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233844"
---
# <a name="expression-evaluation-c"></a>Vyhodnocení výrazu (C)

Výrazy týkající se přiřazení, unárního zvýšení, unárního snížení nebo volání funkce mohou mít následky související s jejich vyhodnocením (vedlejší účinky). Po dosažení „bodu sekvence“ má vše, co předchází tento bod sekvence, včetně jakýchkoli vedlejších účinků, zaručeno vyhodnocení před zahájením vyhodnocení jakéhokoli následujícího bodu sekvence.

„Vedlejší účinky“ jsou změny způsobené vyhodnocením výrazu. K vedlejším účinkům dochází, kdykoli se při vyhodnocení výrazu změní hodnota proměnné. Všechny operace přiřazení mají vedlejší účinky. Volání funkce mohou mít také vedlejší účinky, pokud změní hodnotu externě viditelné položky, buď přímým přiřazením, nebo nepřímým přiřazením prostřednictvím ukazatele.

## <a name="see-also"></a>Viz také:

[Operandy a výrazy](../c-language/operands-and-expressions.md)
