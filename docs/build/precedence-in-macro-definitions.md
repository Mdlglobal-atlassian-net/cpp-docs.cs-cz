---
title: Priority v definicích maker | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, precedence in macro definitions
- macros, precedence
ms.assetid: 0c13182d-83cb-4cbd-af2d-f4c916b62aeb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ce6f0acc898dc719d2252d5cc59dff92bda4a98
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368610"
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