---
title: "Chyba sestavení projektu PRJ0006 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0006
dev_langs: C++
helpviewer_keywords: PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef1dff813c709a117d92abcdd7a2d4f9d3420c65
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0006"></a>Chyba sestavení projektu PRJ0006
Nelze otevřít dočasný soubor 'file'. Ujistěte se, že soubor existuje a že adresář není chráněna proti zápisu.  
  
 Visual C++ nelze vytvořit dočasný soubor během procesu vytváření. Příčiny tohoto stavu:  
  
-   Žádné dočasného adresáře.  
  
-   Jen pro čtení dočasný adresář.  
  
-   Nedostatek místa na disku.  
  
-   $(Intdir) – složka je buď jen pro čtení nebo obsahuje dočasné soubory, které jsou jen pro čtení.  
  
 Tato chyba nastane také následující chyba PRJ0007: Nelze vytvořit adresář' výstupní adresář". Chyba PRJ0007 znamená, že nelze vytvořit adresář $(IntDir), zdání vytváření dočasně souborů se také nezdaří.  
  
 Dočasné soubory se vytvoří vždy, když zadáte:  
  
-   Soubor odezvy.  
  
-   Vlastní krok sestavení.  
  
-   Události sestavení.