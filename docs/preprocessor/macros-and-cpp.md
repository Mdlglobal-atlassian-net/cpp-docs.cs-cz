---
title: Makra a jazyk C++ | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7af092d31fb4495be47c88aaaf8830cc05db2bc7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="macros-and-c"></a>Makra a jazyk C++
Jazyk C++ nabízí nové možnosti, z nichž některé nahrazují možnosti preprocesoru standardu ANSI C. Tyto nové možnosti zvyšují bezpečnost typů a předvídatelnost jazyka:  
  
-   V jazyce C++ objekty deklarován jako **const** mohou být používány konstantní výrazy. To programům umožňuje deklarovat konstanty, které mají informace o typu a hodnotě, a výčty, které lze symbolicky zobrazit ladicím programem. Použití direktivy `#define` preprocesoru pro definování konstant není tak přesné. Žádné úložiště přidělené **const** objektu, pokud výraz, který přebírá adresy se nachází v programu.  
  
-   Schopnost vložených funkcí jazyka C++ nahrazuje makra typů funkce. Výhody použití vložených funkcí oproti makrům jsou:  
  
    -   Bezpečnost typů. Vložené funkce jsou kontrolovány stejně jako normální funkce. Makra nejsou typově bezpečná.  
  
    -   Správná manipulace s argumenty, které mají vedlejší účinky. Vložené funkce vyhodnotí výrazy, které jsou zadány jako argumenty, před vstupem do těla funkce. Proto neexistuje možnost, že by výrazy s vedlejšími účinky byly nebezpečné.  
  
 Další informace o vložených funkcí najdete v tématu [vložené, __inline, \__forceinline](../cpp/inline-functions-cpp.md).  
  
 Z důvodu zpětné kompatibility jsou v jazyce C++ společnosti Microsoft zachovány všechny funkce preprocesoru, které existovaly ve standardu ANSI C a starších specifikacích jazyka C++.  
  
## <a name="see-also"></a>Viz také  
 [Předdefinovaná makra](../preprocessor/predefined-macros.md)   
 [Makra (C/C++)](../preprocessor/macros-c-cpp.md)