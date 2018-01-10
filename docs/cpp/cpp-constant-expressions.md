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
ms.workload: cplusplus
ms.openlocfilehash: 0cd30dd51b3d87b7d82b917734d187ae2278837a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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