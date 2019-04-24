---
title: Chyba linkerů LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: c5cbb9a7159a976ad0f96f46462669cff7b19f26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62213261"
---
# <a name="linker-tools-error-lnk1201"></a>Chyba linkerů LNK1201

Chyba při zápisu do databáze programu 'filename'; kontrolovat nedostatek místa na disku, cesta je neplatná nebo nemáte dostatečná oprávnění

Odkaz nemůže zapisovat do databáze programu (PDB) pro výstupní soubor.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Soubor je poškozený. Odstraňte soubor PDB a znovu připojit.

1. Není dostatek místa na disku pro zápis souboru.

1. Jednotka není k dispozici, pravděpodobně z důvodu potíží se sítí.

1. Ladicí program je aktivní na aplikaci, kterou se snažíte propojit.

1. Nedostatek prostoru v haldě.  Zobrazit [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Další informace.