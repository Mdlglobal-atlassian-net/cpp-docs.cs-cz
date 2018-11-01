---
title: Rekurzivní makra
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 0005a4be0422ed83816eabc7b55932a81441ae25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451256"
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