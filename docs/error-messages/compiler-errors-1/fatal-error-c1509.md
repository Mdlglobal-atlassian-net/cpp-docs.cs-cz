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
ms.workload: cplusplus
ms.openlocfilehash: 22cb22ea2186b16fd98d2714779b2475c51d15bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1509"></a>Závažná chyba C1509
omezení kompilátoru: příliš mnoho stavy obslužné rutiny výjimek ve funkci 'function'. zjednodušení – funkce  
  
 Kód překračuje vnitřní limit na stavy obslužné rutiny výjimek (32 768 stavy).  
  
 Nejčastější příčinou je, že funkce obsahuje složitý výraz uživatelsky definované třídy, proměnných a aritmetické operátory.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Výrazy Zjednodušte přiřazením běžné podvýrazy dočasné proměnné.  
  
2.  Funkce rozdělení na menší funkce.