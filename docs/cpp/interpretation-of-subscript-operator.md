---
title: Interpretace operátoru dolního indexu
ms.date: 08/27/2018
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
ms.openlocfilehash: 1c3d5bca66cb294503805fd5b7691331ac380ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375311"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretace operátoru dolního indexu

Stejně jako ostatní operátory operátor dolního indexu (**\[]**) můžete předeklarovat uživatelem. Výchozí chování operátoru indexu, pokud není přetížen, je kombinování názvu pole a indexu pomocí následující metody:

\*((*název pole*) + (*dolní index*))

Stejně jako všechna sčítání, která zahrnují typy ukazatelů, se změna velikosti provádí automaticky pro úpravu velikosti typu. Proto je výsledná hodnota není *dolní index* bajtů od počátku *název pole*; místo toho je *dolní index*tý prvek pole. (Další informace o tomto převodu naleznete v tématu [operátory součtu](../cpp/additive-operators-plus-and.md).)

Pro vícerozměrná pole je adresa odvozena podobně následujícím způsobem:

((*název pole*) + (*dolní index*1 \* *maximální*2 \* *maximální*3 \* ... \* *maximální*n) + (*dolní index*2 \* *maximální*3 \* ... \* *maximální*n) + … + *dolní index*n))

## <a name="see-also"></a>Viz také:

[Pole](../cpp/arrays-cpp.md)<br/>
