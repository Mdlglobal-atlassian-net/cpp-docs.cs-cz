---
title: "Speciální znaky v souboru pravidel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, special characters
- makefiles, special characters
- special characters, in NMAKE macros
- macros, special characters
ms.assetid: 92c34ab5-ca6b-4fc0-bcf4-3172eaeda9f0
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 53b2457c87e587b4e1ef13e53bf2dfcdd4800d7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="special-characters-in-a-makefile"></a>Speciální znaky v souboru pravidel
Chcete-li použít speciální znak NMAKE jako literál znak, umístěte šipka nahoru (^) úrovních před ním. NMAKE ignoruje carets před dalšími znaky. Speciální znaky jsou:  
  
 `:  ;  #  (  )  $  ^  \  {  }  !  @  —`  
  
 Šipka nahoru (^) v rámci řetězec v uvozovkách považován za znak literálu pomocí kurzoru. Šipka nahoru na konci řádku vloží literálu znaku v řetězci nebo makro.  
  
 V makrech, zpětné lomítko (\\) a potom podle nový řádek nahrazuje znak mezery.  
  
 V příkazech symbol procenta (%) je soubor specifikátor. Chcete-li představují % oznámena v příkazu, zadejte místo jeden Dvojitý znak procenta (%). V jiných situacích NMAKE interpretuje jeden % oznámena, ale vždy interpretuje dvojitou %% jako jeden %. Proto představují literál %%, zadejte buď znaky procenta tři servery %%%, nebo čtyři procent známky servery %%%.  
  
 Chcete-li použít znak dolaru ($) jako literál v příkazu, zadejte dva znaky dolaru ($$). Tuto metodu lze také v jiných situacích, kde ^ $ funguje.  
  
## <a name="see-also"></a>Viz také  
 [Obsah souboru pravidel](../build/contents-of-a-makefile.md)