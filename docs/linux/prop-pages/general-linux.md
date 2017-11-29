---
title: "Obecné vlastnosti (Linux C++ projekt) | Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
ms.openlocfilehash: 4de08a00ddedf1eec97d1872646a986e09c22547
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="general-properties-linux-c"></a>Obecné vlastnosti (Linux C++)

Vlastnost | Popis | Možnosti
--- | ---| ---
Výstupní adresář | Určuje relativní cestu do výstupního adresáře. soubor; může obsahovat proměnné prostředí.
Zprostředkující adresáře | Určuje relativní cestu k adresáři pomocný soubor; může obsahovat proměnné prostředí.
Cílový název | Určuje název souboru, který bude generovat tento projekt.
Přípona cílového | Určuje příponu souboru, která bude vytvářet tento projekt. (Příklad: .a)
Rozšíření k odstranění na vyčištění | Oddělte středníkem oddělené specifikace zástupný znak, pro které soubory v adresáři zprostředkující odstranit na čištění nebo znovu vytvořit.
Vytvoření souboru protokolu | Určuje soubor protokolu sestavení pro zápis, když sestavení protokolování je povolena.
Sada nástrojů platformy | Určuje sada nástrojů používá pro vytváření aktuální konfiguraci; Není-li se používá sada, výchozí sady nástrojů
Počítač vzdáleného sestavení | Cílový počítač nebo zařízení, které chcete použít pro vzdálené sestavení, nasazení a ladění.
Vzdálené sestavení kořenového adresáře | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení.
Adresáři vzdáleného sestavení projektu | Určuje cestu k adresáři na vzdáleném počítači nebo zařízení pro projekt.
Typ konfigurace | Určuje typ výstupu, který generuje tuto konfiguraci. | **Dynamické knihovny (.so)** -dynamické knihovny (.so)<br>**Statické knihovny (.a)** – statické knihovny (.a)<br>**Aplikace (.out)** -aplikace (.out)<br>**Makefile** -souboru pravidel<br>
Použití STL | Určuje, které standardní knihovna C++ pro tuto konfiguraci. | **Sdílené GNU standardní knihovna C++**<br>**Standardní knihovna C++ statické GNU (-statické)**<br>