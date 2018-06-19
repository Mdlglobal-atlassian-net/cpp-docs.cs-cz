---
title: Speciální znaky v makrech | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c271d2f39a4d81776c06a107616170192e82d40d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380170"
---
# <a name="special-characters-in-macros"></a>Speciální znaky v makrech
Číslo přihlásit (#), po definici určuje komentář. Pokud chcete zadat literálu znaménko čísla v makru, použijte šipka nahoru (^), jako v ^ #.  
  
 Znak dolaru ($) určuje makro volání. Pokud chcete zadat literálu $, použijte $$.  
  
 K rozšíření definice na nový řádek, ukončení řádku obráceným lomítkem (\\). Po vyvolání makro znak zpětného lomítka plus nový řádek nahrazuje mezerami. Pokud chcete zadat literálu zpětné lomítko na konci řádku, uveďte před ním šipka nahoru (^) nebo po ní následuje specifikátor komentář (#).  
  
 K určení znaku literálu nový řádek, ukončete řádek s šipka nahoru (^), stejně jako na:  
  
```  
CMDS = cls^  
dir  
```  
  
## <a name="see-also"></a>Viz také  
 [Definice makra NMAKE](../build/defining-an-nmake-macro.md)