---
title: "Závažná chyba C1509 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1509
dev_langs: C++
helpviewer_keywords: C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3d3fc7a7be867a7137dab4155984cf1844b661ea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509
omezení kompilátoru: příliš mnoho stavy obslužné rutiny výjimek ve funkci 'function'. zjednodušení – funkce  
  
 Kód překračuje vnitřní limit na stavy obslužné rutiny výjimek (32 768 stavy).  
  
 Nejčastější příčinou je, že funkce obsahuje složitý výraz uživatelsky definované třídy, proměnných a aritmetické operátory.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Výrazy Zjednodušte přiřazením běžné podvýrazy dočasné proměnné.  
  
2.  Funkce rozdělení na menší funkce.