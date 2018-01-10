---
title: "Priority v definicích maker | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7421ef51c37e3724bdb986321581e6736a62e18b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="precedence-in-macro-definitions"></a>Priority v definicích maker
Pokud makra má několik definic, používá NMAKE definici nejvyšší prioritou. V následujícím seznamu jsou uvedeny pořadí podle priority, od nejvyšší po nejnižší:  
  
1.  Makro definované na příkazovém řádku  
  
2.  Makro definované v souboru pravidel nebo zahrnout soubor  
  
3.  Makro aplikace zděděné proměnné prostředí  
  
4.  Makro definované v souboru Tools.ini  
  
5.  Předdefinovaná makra, jako například [kopie](../build/command-macros-and-options-macros.md) a [AS](../build/command-macros-and-options-macros.md)  
  
 Pomocí /E makra zděděno z proměnných prostředí k přepsání souboru pravidel makra se stejným názvem. Použití **! UNDEF** přepsat příkazového řádku.  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)