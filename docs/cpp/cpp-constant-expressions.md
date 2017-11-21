---
title: "Výrazy konstant v jazyce C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9f6961e210af254cd807b133e034610f03ca866e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-constant-expressions"></a>Výrazy konstant v jazyce C++
A *konstantní* hodnota je 1, která se nemění. C++ poskytuje dva klíčová slova, která vám umožní express záměr, že má být změněn a k vynucení tohoto záměru není určen objekt.  
  
 C++ vyžaduje konstantní výrazy – výrazy, která se vyhodnotí jako konstanta – pro deklarace:  
  
-   Meze pole  
  
-   Selektory v case – příkazy  
  
-   Specifikace délky bitová pole  
  
-   Inicializátory – výčet  
  
 Pouze operandy, které jsou přípustné v konstantní výrazy jsou:  
  
-   Literály  
  
-   Konstanty výčtu  
  
-   Hodnoty deklarován jako const, která jsou inicializovány s konstantní výrazy  
  
-   `sizeof`výrazy  
  
 Nonintegral konstanty musí být převeden (explicitně nebo implicitně) na integrální typy jako právní v konstantní výraz. Proto je platný následující kód:  
  
```  
const double Size = 11.0;  
char chArray[(int)Size];  
```  
  
 Explicitní převody na integrální typy jsou právní v konstantní výrazy; všechny ostatní typy a odvozené typy jsou neplatné kromě při používat jako operandy k `sizeof` operátor.  
  
 Operátor čárky a operátory přiřazení nelze použít v konstantní výrazy.  
  
## <a name="see-also"></a>Viz také  
 [Typy výrazů](../cpp/types-of-expressions.md)