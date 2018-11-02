---
title: Upozornění linkerů LNK4206
ms.date: 12/05/2017
f1_keywords:
- LNK4206
helpviewer_keywords:
- LNK4206
ms.assetid: 6c108e33-00cf-4c5a-830d-d65d470930a7
ms.openlocfilehash: dc81df89609f59834c8a3271dd64f3b99b281f90
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613634"
---
# <a name="linker-tools-warning-lnk4206"></a>Upozornění linkerů LNK4206

> Předkompilované informace o typu nebyl nalezen. "*filename*" není propojený nebo přepsat; objekt se propojí, jako by nebyly dostupné žádné ladicí informace

*Filename* soubor objektu zkompilován s použitím [/Yc](../../build/reference/yc-create-precompiled-header-file.md), buď v příkazu LINK nebyl zadán nebo byl přepsán.

Běžný scénář pro toto upozornění je při .obj, který byl kompilován s možností/Yc je uložený v knihovně, a pokud neexistují žádné odkazy na symboly do tohoto .obj z vašeho kódu.  V takovém případě linkeru nebude používat (nebo dokonce vidět) souboru .obj.  V takovém případě by měl váš kód znovu zkompilovat a použít [/Yl](../../build/reference/yl-inject-pch-reference-for-debug-library.md) pro objekty zkompilovanými s použitím [/Yu](../../build/reference/yu-use-precompiled-header-file.md).