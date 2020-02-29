---
title: Obecné vlastnosti projektů (soubor pravidel pro Android C++)
ms.date: 10/23/2017
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
f1_keywords:
- VC.Project.VCConfiguration.Android.Makefile.OutputDirectory
- VC.Project.VCConfiguration.Android.Makefile.IntermediateDirectory
- VC.Project.VCConfiguration.Android.Makefile.BuildLogFile
- VC.Project.VCConfiguration.Android.Makefile.ConfigurationType
ms.openlocfilehash: a52cedb1f7f7af1d4a0ff8e1a0d766d6e769e2fa
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177415"
---
# <a name="general-project-properties-android-c-makefile"></a>Obecné vlastnosti projektu (soubor C++ pravidel pro Android)

Vlastnost | Popis | Vlastnit
--- | ---| ---
Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí.
Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí.
Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení.
Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna ( *. so*)<br>**Statická knihovna (. a)** – statická knihovna ( *. a*)<br>**Nástroj** – nástroj<br>**Makefile** -makefile<br>
