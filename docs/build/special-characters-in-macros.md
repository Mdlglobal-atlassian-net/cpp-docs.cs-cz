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
ms.workload: cplusplus
ms.openlocfilehash: 4d954abc593fcba3887da4f7ee4bd5ce1e443e18
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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