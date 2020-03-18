---
title: Obecné vlastnosti projektů (Android C++)
ms.date: 10/23/2017
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
f1_keywords:
- VC.Project.VCConfiguration.Android.OutputDirectory
- VC.Project.VCConfiguration.Android.IntermediateDirectory
- VC.Project.VCConfiguration.Android.TargetName
- VC.Project.VCConfiguration.Android.TargetExt
- VC.Project.VCConfiguration.Android.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.Android.BuildLogFile
- VC.Project.VCConfiguration.Android.PlatformToolset
- VC.Project.VCConfiguration.Android.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: 78f6df8286151b61ed026cc6b5170ff3508295d4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446883"
---
# <a name="general-project-properties-android-c"></a>Obecné vlastnosti projektů (Android C++)

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí. |
| Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí. |
| Cílový název | Určuje název souboru, který tento projekt vygeneruje. |
| Cílová Přípona | Určuje příponu souboru, kterou tento projekt vygeneruje. (Příklad: *. exe* nebo *. dll*) |
| Přípony k odstranění při čištění | Středníky oddělená specifikace zástupných znaků, pro které se soubory v zprostředkujícím adresáři odstraňují při čištění nebo opětovném sestavení. |
| Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení. |
| Sada nástrojů platformy | Určuje sadu nástrojů použitou pro sestavení aktuální konfigurace. Pokud není nastavená, použije se výchozí sada nástrojů. |
| Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna ( *. so*)<br>**Statická knihovna (. a)** – statická knihovna ( *. a*)<br>**Nástroj** – nástroj<br>**Makefile** -makefile<br> |
| Cílová úroveň rozhraní API | Úroveň rozhraní API pro Android NDK, na kterou cílí Tato konfigurace. |
| Použití STL | Určuje, C++ která standardní knihovna se má použít pro tuto konfiguraci. | **Minimální C++ běhová knihovna (systém)**<br>**C++Statická knihovna modulu runtime (Gabi + + _static)**<br>**C++Běhová knihovna Shared (Gabi + + _shared)**<br>**Statická knihovna sdílená knihovna běhového runtime (stlport_static)**<br>**Sdílená knihovna sdílená knihovna běhového runtime (stlport_shared)**<br>**Statická knihovna GNU STL (gnustl_static)**<br>**Sdílená knihovna GNU STL (gnustl_shared)**<br>**Statická knihovna LLVM libc + + (c++ _static)**<br>**Sdílená knihovna LLVM libc + + (c++ _shared)**<br> |
| Režim miniatur | Vygeneruje kód, který se spustí pro mikroarchitekturu pro palec. To platí jenom pro architekturu ARM. | **Táhl**<br>**ARM**<br>**Disabled** (Zakázáno)<br> |
