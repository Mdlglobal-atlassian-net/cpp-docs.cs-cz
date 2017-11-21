---
title: "Speciální znaky v makrech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 648122a9c8f3cf97d08128e6e12090ebc12631d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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