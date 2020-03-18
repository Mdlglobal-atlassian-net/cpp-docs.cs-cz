---
title: Obecné vlastnosti projektů (soubor pravidel pro Android C++)
ms.date: 10/23/2017
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
f1_keywords:
- VC.Project.VCConfiguration.Android.Makefile.OutputDirectory
- VC.Project.VCConfiguration.Android.Makefile.IntermediateDirectory
- VC.Project.VCConfiguration.Android.Makefile.BuildLogFile
- VC.Project.VCConfiguration.Android.Makefile.ConfigurationType
ms.openlocfilehash: 0d03cff6b202f554e9829c51b35f069ae61576de
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446876"
---
# <a name="general-project-properties-android-c-makefile"></a>Obecné vlastnosti projektu (soubor C++ pravidel pro Android)

| Vlastnost | Popis | Vlastnit |
|--|--|--|
| Výstupní adresář | Určuje relativní cestu k adresáři výstupního souboru. může obsahovat proměnné prostředí. |
| Zprostředkující adresář | Určuje relativní cestu k adresáři zprostředkujícího souboru. může obsahovat proměnné prostředí. |
| Soubor protokolu sestavení | Určuje soubor protokolu sestavení, do kterého se má zapisovat, pokud je povolené protokolování sestavení. |
| Typ konfigurace | Určuje typ výstupu, který tato konfigurace generuje. | **Dynamická knihovna (. so)** – dynamická knihovna ( *. so*)<br>**Statická knihovna (. a)** – statická knihovna ( *. a*)<br>**Nástroj** – nástroj<br>**Makefile** -makefile<br> |
