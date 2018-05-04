---
title: Interpretace operátoru dolního indexu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9bba312c6969acf95be8899f58f65e31c75386c4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="interpretation-of-subscript-operator"></a>Interpretace operátoru dolního indexu
Jako další operátory operátor dolního indexu (**[]**) může být změněna uživatelem. Výchozí chování operátoru indexu, pokud není přetížen, je kombinování názvu pole a indexu pomocí následující metody:  
  
 \*((*název pole*) + (*dolní index*))  
  
 Stejně jako všechna sčítání, která zahrnují typy ukazatelů, se změna velikosti provádí automaticky pro úpravu velikosti typu. Proto výsledná hodnota není *dolní index* bajtů z původu *název pole*; místo toho je *dolní index*element TD pole. (Další informace o tento převod najdete v tématu [doplňkové operátory](../cpp/additive-operators-plus-and.md).)  
  
 Pro vícerozměrná pole je adresa odvozena podobně následujícím způsobem:  
  
 **((**   
 ***Název pole* ) + ()**   
 ***dolní index* 1***maximální*2  *\* maximální*3 *.. .max*n) **+** *dolní index*2  *\* maximální*3 *.. .max*n).   . . *+* *dolní index*n))  
  
## <a name="see-also"></a>Viz také  
 [Pole](../cpp/arrays-cpp.md)