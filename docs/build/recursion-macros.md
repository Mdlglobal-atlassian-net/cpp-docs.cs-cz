---
title: "Rekurzivní makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e8d9ef7f194151fb3259712759d0c29ed157d564
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recursion-macros"></a>Rekurzivní makra
Rekurzivní makra využít k volání NMAKE rekurzivně. Rekurzivní relace dědit informace o Tools.ini a makra příkazového řádku a proměnnou prostředí. Nedědí definované makefile odvozená pravidla nebo **. PŘÍPONY** a **. DRAHOCENNÝ** specifikace. Předávání makra NMAKE relaci rekurzivní, nastavit proměnnou prostředí s NASTAVENÝM před voláním rekurzivní, definujte makro v příkazu pro rekurzivní volání nebo definování makra v Tools.ini.  
  
|– Makro|Definice|  
|-----------|----------------|  
|**UJISTĚTE SE**|Příkaz původně použije k vyvolání NMAKE.<br /><br /> Makro $(MAKE) poskytuje úplnou cestu k nmake.exe.|  
|**MAKEDIR –**|Pokud byl vyvolán NMAKE aktuální adresář.|  
|**MAKEFLAGS**|Možnosti právě vliv. Použít jako `/$(MAKEFLAGS)`.  Všimněte si, /F není zahrnutý.|  
  
## <a name="see-also"></a>Viz také  
 [Speciální makra NMAKE](../build/special-nmake-macros.md)