---
title: Upozornění linkerů LNK4099
ms.date: 11/04/2016
f1_keywords:
- LNK4099
helpviewer_keywords:
- LNK4099
ms.assetid: 358170a4-07cd-43fe-918f-82c32757ffc5
ms.openlocfilehash: b1f330924b8e47e0649268142106a050c83cb20a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183316"
---
# <a name="linker-tools-warning-lnk4099"></a>Upozornění linkerů LNK4099

Soubor PDB s názvem "Object/Library" nebo "path" nebyl nalezen. propojování objektu, jako by nebyly žádné ladicí informace

Linker nemohl najít soubor. pdb. Zkopírujte ho do adresáře, který obsahuje `object/library`.

Chcete-li najít název souboru PDB přidruženého k souboru objektu:

1. Extrahujte soubor objektu z knihovny pomocí [lib](../../build/reference/lib-reference.md) **/Extract:** `objectname` **. obj** `xyz` **. lib**.

1. Ověřte cestu k souboru. pdb pomocí **dumpbin/section:. debug $ T/rawdata** `objectname` **. obj**.

Můžete také kompilovat pomocí [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md), takže soubor PDB není nutné použít, nebo pokud nemáte soubory. PDB pro objekty, které propojujete, odebrat možnost linkeru [/Debug](../../build/reference/debug-generate-debug-info.md) .
