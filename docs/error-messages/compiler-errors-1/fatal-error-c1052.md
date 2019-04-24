---
title: Závažná chyba C1052
ms.date: 05/08/2017
f1_keywords:
- C1052
helpviewer_keywords:
- C1052
ms.assetid: f2c09a2f-d3c1-4420-9501-ffcb65caf87b
ms.openlocfilehash: b381cc3cfe27d4c4a9d744a6b854a0e43727fe71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243664"
---
# <a name="fatal-error-c1052"></a>Závažná chyba C1052

> soubor databáze programu "*filename*', byl vygenerován linkerem s/Debug: fastlink; kompilátor nemůže takovéto soubory PDB aktualizovat, odstraňte jej nebo použijte parametr /Fd a zadejte jiný název souboru PDB

Kompilátor nemůže aktualizovat stejné soubory databáze (PDB) programu, které se generují pomocí linkeru při [/Debug: fastlink](../../build/reference/debug-generate-debug-info.md) je zadána možnost. Soubory generované kompilátorem PDB a soubory PDB linkerem generovaných obvykle mít odlišné názvy. Pokud jsou nastavená na stejné názvy, může dojít k této chybě.

Chcete-li vyřešit tento problém, explicitně lze odstranit soubory PDB předtím, než znovu zkompilovat, nebo můžete vytvořit různé názvy souborů PDB vygenerovaný kompilátorem a vytvořeného v propojovacím programu.

Chcete-li zadat název souboru PDB generované kompilátorem v příkazovém řádku, použijte [/Fd](../../build/reference/fd-program-database-file-name.md) – možnost kompilátoru. Chcete-li zadat název souboru PDB generované kompilátorem v integrovaném vývojovém prostředí, otevřete **stránky vlastností** dialogové okno pro váš projekt a **vlastnosti konfigurace**, **C/C++**,  **Výstupní soubory** nastavte **název souboru databáze programu** vlastnost. Ve výchozím nastavení, tato vlastnost je `$(IntDir)vc$(PlatformToolsetVersion).pdb`.

Alternativně můžete nastavit název souboru PDB vytvořeného v propojovacím programu. Chcete-li zadat název souboru PDB vytvořeného v propojovacím programu na příkazovém řádku, použijte [/PDB](../../build/reference/pdb-use-program-database.md) – možnost linkeru. Chcete-li zadat název souboru PDB vytvořeného v propojovacím programu v prostředí IDE, otevřete **stránky vlastností** dialogové okno pro váš projekt a **vlastnosti konfigurace**, **Linkeru**,  **Ladění** nastavte **generovat soubor databáze programu** vlastnost. Ve výchozím nastavení, tato vlastnost nastavena na `$(OutDir)$(TargetName).pdb`.
