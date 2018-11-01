---
title: Upozornění linkerů LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: dcf4d44c3a0b5b10035af763040c2912afc8c6f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442171"
---
# <a name="linker-tools-warning-lnk4099"></a>Upozornění linkerů LNK4099

Soubor PDB 'filename' nebyl nalezen 'objektu/knihovny' nebo 'path'; objekt se propojí, jako by nebyly dostupné žádné ladicí informace

Propojovací program nemohl najít soubor .pdb. Zkopírujte do adresáře, který obsahuje `object/library`.

Chcete-li najít název souboru PDB přidružené k souboru objektu:

1. Extrahujte soubor objektu v knihovně s [lib](../../build/reference/lib-reference.md) **/extrahovat:**`objectname`**.obj** `xyz` **lib**.

1. Zkontrolujte cestu k souboru .pdb s **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.

Může také kompilovat s [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), takže se soubor pdb není nutné použít nebo odebrat [/DEBUG](../../build/reference/debug-generate-debug-info.md) – možnost linkeru Pokud nemají soubory .pdb pro objekty, které se připojujete.