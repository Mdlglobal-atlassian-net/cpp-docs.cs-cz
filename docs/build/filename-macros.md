---
title: Makra názvů souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e28ba5923d8b62973860c0ba503d13682b3c5e79
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="filename-macros"></a>Makra názvů souborů
Makra názvů souborů jsou předdefinovány jako názvy souborů zadaný v závislost (specifikace není úplný název souboru na disku). Tyto makra nemusíte být uzavřená v závorkách při vyvolání; jak je znázorněno, zadejte pouze $.  
  
|– Makro|Význam|  
|-----------|-------------|  
|**$@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný.|  
|**$$@**|Aktuální cíl úplný název (cesta, základní název rozšíření), jak je aktuálně zadaný. Platné pouze jako závislé v závislost.|  
|**$&#42;**|Aktuální cíl cestu a základní název bez přípony souboru.|  
|**$&#42;&#42;**|Všechny položky závislé na aktuální cíle.|  
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
