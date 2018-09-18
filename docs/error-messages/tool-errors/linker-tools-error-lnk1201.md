---
title: Chyba Linkerů LNK1201 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c133748f95846160e1387e31e023d9ce459b281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055257"
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