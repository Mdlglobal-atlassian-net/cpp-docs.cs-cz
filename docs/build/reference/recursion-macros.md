---
title: Rekurzivní makra
description: Popisuje makra, která používáte pro volání nástroje NMAKE v rekurzivních relacích.
ms.date: 11/20/2019
helpviewer_keywords:
- NMAKE program, recursion macros
- recursion macros
- macros, recursion
ms.assetid: c53e5ae7-619e-46b1-bdc2-86d8c7798b1d
no-loc:
- MAKE
- MAKEDIR
- MAKEFLAGS
ms.openlocfilehash: f2bda23cb079e4fd7d12cea3598d33b3625c088d
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303153"
---
# <a name="recursion-macros"></a>Rekurzivní makra

Použijte makra rekurze k rekurzivnímu volání NMAKE. Rekurzivní relace dědí makra z příkazového řádku a prostředí a informace o nástrojích. ini. Nedědí pravidla odvození podle souborů pravidel ani `.SUFFIXES` a `.PRECIOUS` specifikace. Existují tři způsoby, jak předat makra rekurzivní relaci NMAKE: před rekurzivním volání nastavte proměnnou prostředí pomocí příkazu :::no-loc text="SET":::. Definujte makro v příkazu pro rekurzivní volání. Nebo definujte makro v souboru Tools. ini.

|– Makro|Definice|
|-----------|----------------|
|**MAKE**|Příkaz, který byl původně použit k vyvolání NMAKE.<br /><br /> Makro `$(MAKE)` poskytuje úplnou cestu k nástroji NMAKE. exe.|
|**MAKEDIR**|Aktuální adresář při vyvolání NMAKE|
|**MAKEFLAGS**|Aktuálně platné možnosti. Použijte jako `/$(MAKEFLAGS)`. Možnost **/f** není zahrnutá.|

## <a name="see-also"></a>Viz také:

[Speciální makra NMAKE](special-nmake-macros.md)
