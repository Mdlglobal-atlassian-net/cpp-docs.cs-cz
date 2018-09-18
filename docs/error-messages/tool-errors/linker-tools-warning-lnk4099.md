---
title: Upozornění Linkerů LNK4099 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4099
dev_langs:
- C++
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50bdceaba2e72312febec4819b96df334b5398c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025998"
---
# <a name="linker-tools-warning-lnk4099"></a>Upozornění linkerů LNK4099

Soubor PDB 'filename' nebyl nalezen 'objektu/knihovny' nebo 'path'; objekt se propojí, jako by nebyly dostupné žádné ladicí informace

Propojovací program nemohl najít soubor .pdb. Zkopírujte do adresáře, který obsahuje `object/library`.

Chcete-li najít název souboru PDB přidružené k souboru objektu:

1. Extrahujte soubor objektu v knihovně s [lib](../../build/reference/lib-reference.md) **/extrahovat:**`objectname`**.obj** `xyz` **lib**.

1. Zkontrolujte cestu k souboru .pdb s **dumpbin /section:.debug$ T /rawdata** `objectname` **.obj**.

Může také kompilovat s [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), takže se soubor pdb není nutné použít nebo odebrat [/DEBUG](../../build/reference/debug-generate-debug-info.md) – možnost linkeru Pokud nemají soubory .pdb pro objekty, které se připojujete.