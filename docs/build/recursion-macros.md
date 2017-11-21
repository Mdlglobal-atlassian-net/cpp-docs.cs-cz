---
title: "Rekurzivní makra | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 41354c34fb21da7f568718489495991cbd1bae43
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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