---
title: Rekurzivní makra | Dokumentace Microsoftu
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
ms.openlocfilehash: f91a5f327686a522608b6eec9fd7106cbab00028
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702037"
---
# <a name="recursion-macros"></a>Rekurzivní makra

Rekurzivní makra použijte k volání NMAKE rekurzivně. Rekurzivní relace dědit z příkazového řádku nebo proměnné prostředí makra a Tools.ini informace. Nedědí odvozených pravidel definovaných pravidel nebo **. PŘÍPONY** a **. CENNÝ** specifikace. Předání makra NMAKE relace rekurzivní nastavení proměnné prostředí se SADOU před rekurzivní volání, definujte makro v příkazu pro rekurzivní volání nebo definujte makro Tools.ini.

|– Makro|Definice|
|-----------|----------------|
|**UJISTĚTE SE**|Příkaz původně použít k vyvolání NMAKE.<br /><br /> Makra $(MAKE) poskytuje úplnou cestu k nmake.exe.|
|**MAKEDIR –**|Aktuální adresář při NMAKE.|
|**MAKEFLAGS**|Možnosti aktuálně používána. Použít jako `/$(MAKEFLAGS)`.  Mějte na paměti, /F produkt není zahrnutý.|

## <a name="see-also"></a>Viz také

[Speciální makra NMAKE](../build/special-nmake-macros.md)