---
title: Rekurzivní makra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2759deaff6014cbba40c97f9d627baf6a800732f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32368958"
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