---
title: "Archiv vzdálených vlastnosti (C++ Linux) | Microsoft Docs"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.Ar.CreateIndex
- VC.Project.Ar.CreateThinArchive
- VC.Project.Ar.NoWarnOnCreate
- VC.Project.Ar.TruncateTimestamp
- VC.Project.Ar.SuppressStartupBanner
- VC.Project.Ar.Verbose
- vc.project.AdditionalOptionsPage
- VC.Project.Ar.OutputFile
- VC.Project.VCConfiguration.BuildLogFile
ms.openlocfilehash: 402fa1f752b311014c828027e45a92a3dc6a2917
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="remote-archive-properties-c-linux"></a>Archiv vzdálených vlastnosti (C++ Linux)

Vlastnost | Popis
--- | ---
Vytvoření indexu archivu | Vytvoření indexu archivu (viz ranlib).  To lze urychlit propojení a snížit závislosti v rámci vlastní knihovny.
Vytvořit dynamické archivu | Vytvořte dynamické archivu.  Dynamické archivu obsahuje relativepaths k objektům místo vkládání objektů.  Přepínání mezi tenký a obvykle vyžaduje odstranění existující knihovnu.
Vytvoření bez upozornění na | Bez varování, pokud knihovny vytvoření.
Zkrácení časové razítko | Použijte pro časová razítka a UID/gids nula.
Potlačit úvodní nápis při spouštění | Dont zobrazit číslo verze.
Verbose | Verbose
Další možnosti | Další možnosti.
Výstupní soubor | / Out možnost přepíše výchozí název a umístění program, který vytvoří lib.
Archiver | Určuje program, který má být vyvolán při propojování statické objekty nebo cestu k archiver ve vzdáleném systému.
Časový limit archiver | Časový limit vzdálené archiver, v milisekundách.
Kopírovat výstup | Určuje, jestli zkopírujte výstupní soubor sestavení ze vzdáleného systému v místním počítači.
