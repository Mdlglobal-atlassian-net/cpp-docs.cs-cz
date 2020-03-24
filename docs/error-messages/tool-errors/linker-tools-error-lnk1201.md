---
title: Chyba linkerů LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195107"
---
# <a name="linker-tools-error-lnk1201"></a>Chyba linkerů LNK1201

Chyba při zápisu do databáze programu filename; kontrolovat nedostatek místa na disku, neplatná cesta nebo nedostatečné oprávnění

ODKAZ nemůže zapisovat do databáze programu (PDB) pro výstupní soubor.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Soubor je poškozen. Odstraňte soubor PDB a znovu ho připojte.

1. Nedostatek místa na disku pro zápis souboru.

1. Jednotka není k dispozici, pravděpodobně v důsledku problému se sítí.

1. Ladicí program je aktivní v programu, který se pokoušíte propojit.

1. Nedostatek prostoru v haldě.  Další informace najdete v tématu [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
