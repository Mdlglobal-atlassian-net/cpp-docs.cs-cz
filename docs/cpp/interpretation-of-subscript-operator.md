---
title: Interpretace operátoru dolního indexu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- subscript operator [C++], interpretation of
- arrays [C++], subscripting
- interpreting subscript operators [C++]
- operators [C++], interpretation of subscript
ms.assetid: 8852ca18-9d5b-43f7-b8bd-abc89364fbf2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0eeb8d4232fae16cfaa588341a54bf4318483b92
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43213428"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretace operátoru dolního indexu

Stejně jako ostatní operátory operátor dolního indexu (**\[]**) můžete předeklarovat uživatelem. Výchozí chování operátoru indexu, pokud není přetížen, je kombinování názvu pole a indexu pomocí následující metody:

\*((*název pole*) + (*dolní index*))

Stejně jako všechna sčítání, která zahrnují typy ukazatelů, se změna velikosti provádí automaticky pro úpravu velikosti typu. Proto je výsledná hodnota není *dolní index* bajtů od počátku *název pole*; místo toho je *dolní index*tý prvek pole. (Další informace o tomto převodu naleznete v tématu [operátory součtu](../cpp/additive-operators-plus-and.md).)

Pro vícerozměrná pole je adresa odvozena podobně následujícím způsobem:

((*název pole*) + (*dolní index*1 \* *maximální*2 \* *maximální*3 \* ... \* *maximální*n) + (*dolní index*2 \* *maximální*3 \* ... \* *maximální*n) + … + *dolní index*n))  
  
## <a name="see-also"></a>Viz také:

[Pole](../cpp/arrays-cpp.md)<br/>
