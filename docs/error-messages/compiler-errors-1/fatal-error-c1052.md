---
title: "Závažná chyba C1052 | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1052
dev_langs: C++
helpviewer_keywords: C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
caps.latest.revision: "0"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a64caf82dcc99a26d7eb46d6e27465b0a8976edb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1052"></a>Závažná chyba C1052  
  
> soubor databáze programu '*filename*', vygenerovalo linkeru s /DEBUG:fastlink; kompilátoru nelze aktualizovat tyto soubory PDB; prosím odstraňte ji nebo zadejte jiný název souboru PDB pomocí /Fd  
  
Kompilátor nelze aktualizovat stejné soubory databáze (PDB) programu, které jsou generované linkeru při [/DEBUG:fastlink](../../build/reference/debug-generate-debug-info.md) je zadána možnost. Za normálních okolností PDB soubory generované kompilátorem a PDB soubory generované linkeru mít odlišné názvy. Pokud jsou nastavená používat stejné názvy, může vést k této chybě.  
  
Chcete-li tento problém vyřešit, můžete explicitně odstranit soubory PDB před zkompilujete znovu, nebo můžete vytvořit různé názvy pro soubory PDB generované kompilátorem a generované linkeru.  
  
Chcete-li název souboru PDB generované kompilátorem zadejte na příkazovém řádku, použijte [/Fd](../../build/reference/fd-program-database-file-name.md) – možnost kompilátoru. Chcete-li zadat název souboru PDB generované kompilátorem v prostředí IDE, otevřete **stránky vlastností** dialogové okno pro svůj projekt a v **vlastnosti konfigurace**, **C/C++**,  **Výstupní soubory** nastavte **název souboru databáze programu** vlastnost. Ve výchozím nastavení, tato vlastnost je `$(IntDir)vc$(PlatformToolsetVersion).pdb`.  
  
Alternativně můžete nastavit název souboru PDB generované linkeru. Chcete-li zadat název souboru PDB generované linkeru na příkazovém řádku, použijte [/PDB](../../build/reference/pdb-use-program-database.md) – možnost linkeru. Chcete-li zadat název souboru PDB generované linkeru v prostředí IDE, otevřete **stránky vlastností** dialogové okno pro svůj projekt a v **vlastnosti konfigurace**, **Linkeru**,  **Ladění** nastavte **generování souboru databáze programu** vlastnost. Ve výchozím nastavení je tato vlastnost nastavena `$(OutDir)$(TargetName).pdb`.  