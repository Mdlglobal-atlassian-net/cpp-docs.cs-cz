---
title: "Bloky popisů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cec8005599ab6d4e2b7d769f73b5ef2e3869accd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="description-blocks"></a>Bloky popisů
Popis blok je řádek závislostí a za blok příkazů:  
  
```  
targets... : dependents...  
    commands...  
```  
  
 Řádek závislostí Určuje jeden nebo více cílů a nula nebo více závislé objekty. Cíl musí být na začátek řádku. Samostatné cíle z položky závislé na dvojtečkou (:); mezery nebo karty jsou povoleny. Rozdělit čáru, použijte po cíl a závislé na zpětné lomítko (\). Cíl neexistuje, má starší časové razítko než závislé, zda je [pseudotarget](../build/pseudotargets.md), NMAKE provede příkazy. Pokud závislé je cílem jinde a neexistuje nebo je zastaralé s ohledem na svůj vlastní závislé objekty, aktualizuje NMAKE závislé před aktualizací aktuální závislost.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
 [Cíle](../build/targets.md)  
  
 [Závislé objekty](../build/dependents.md)  
  
## <a name="see-also"></a>Viz také  
 [NMAKE – odkaz](../build/nmake-reference.md)