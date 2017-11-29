---
title: "Makra názvů souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: faa791e75817e3845b0f445cc741c88b7461a7c5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="filename-macros"></a>Makra názvů souborů
Makra názvů souborů jsou předdefinovány jako názvy souborů zadaný v závislost (specifikace není úplný název souboru na disku). Tyto makra nemusíte být uzavřená v závorkách při vyvolání; jak je znázorněno, zadejte pouze $.  
  
|– Makro|Význam|  
|-----------|-------------|  
|**$@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný.|  
|**$$@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný. Platné pouze jako závislé v závislost.|  
|**$\***|Aktuální cíl cestu a základní název bez přípony souboru.|  
|**$\*\***|Všechny položky závislé na aktuální cíle.|  
|**$?**|Všechny závislé objekty s časovým razítkem novější než aktuální cíl.|  
|**$<**|Závislý soubor s časovým razítkem novější než aktuální cíl. Platné jenom v příkazech v odvozených pravidlech.|  
  
 Pokud chcete zadat části makra předdefinované název souboru, připojit modifikátor – makro a uzavřete upravené makro v závorkách.  
  
|Modifikátor|Výsledná část názvu souboru|  
|--------------|-----------------------------|  
|**D**|Jednotky a adresáře|  
|**B**|Základní název|  
|**F**|Základního názvu plus rozšíření|  
|**R**|Jednotka plus directory plus základní název|  
  
## <a name="see-also"></a>Viz také  
 [Speciální makra NMAKE](../build/special-nmake-macros.md)