---
title: Interpretace operátoru dolního indexu | Dokumentace Microsoftu
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
ms.openlocfilehash: 75659730198e09a172625c54bfcbdd54b7a9f857
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404785"
---
# <a name="interpretation-of-subscript-operator"></a>Interpretace operátoru dolního indexu
Stejně jako ostatní operátory operátor dolního indexu (**[] č.**) můžete předeklarovat uživatelem. Výchozí chování operátoru indexu, pokud není přetížen, je kombinování názvu pole a indexu pomocí následující metody:  
  
 \*((*název pole*) + (*dolní index*))  
  
 Stejně jako všechna sčítání, která zahrnují typy ukazatelů, se změna velikosti provádí automaticky pro úpravu velikosti typu. Proto je výsledná hodnota není *dolní index* bajtů od počátku *název pole*; místo toho je *dolní index*tý prvek pole. (Další informace o tomto převodu naleznete v tématu [operátory součtu](../cpp/additive-operators-plus-and.md).)  
  
 Pro vícerozměrná pole je adresa odvozena podobně následujícím způsobem:  
  
 **((**   
 ***Název pole* ) + ()**   
 ***dolní index* 1***maximální*2  *\* maximální*3 *.. .max*n) **+** *dolní index*2  *\* maximální*3 *.. .max*n).   . . *+* *dolní index*n))  
  
## <a name="see-also"></a>Viz také:  
 [Pole](../cpp/arrays-cpp.md)