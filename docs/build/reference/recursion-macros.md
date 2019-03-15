---
title: Rekurzivní makra
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
ms.openlocfilehash: 064bc40906bcf3a126c225585a6df43443b5c38e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823429"
---
# <a name="recursion-macros"></a>Rekurzivní makra

Rekurzivní makra použijte k volání NMAKE rekurzivně. Rekurzivní relace dědit z příkazového řádku nebo proměnné prostředí makra a Tools.ini informace. Nedědí odvozených pravidel definovaných pravidel nebo **. PŘÍPONY** a **. CENNÝ** specifikace. Předání makra NMAKE relace rekurzivní nastavení proměnné prostředí se SADOU před rekurzivní volání, definujte makro v příkazu pro rekurzivní volání nebo definujte makro Tools.ini.

|– Makro|Definice|
|-----------|----------------|
|**UJISTĚTE SE**|Příkaz původně použít k vyvolání NMAKE.<br /><br /> Makra $(MAKE) poskytuje úplnou cestu k nmake.exe.|
|**MAKEDIR –**|Aktuální adresář při NMAKE.|
|**MAKEFLAGS**|Možnosti aktuálně používána. Použít jako `/$(MAKEFLAGS)`.  Mějte na paměti, /F produkt není zahrnutý.|

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](special-nmake-macros.md)
