---
title: Pseudocíle
ms.date: 11/04/2016
helpviewer_keywords:
- makefiles, pseudotargets
- pseudotargets and NMAKE
- NMAKE program, pseudotargets
- timestamps, makefile pseudotargets
- NMAKE program, targets
ms.assetid: c8c479dc-0129-4186-8366-bc6251f2b494
ms.openlocfilehash: 90552d00aaeed804f2bf492a94493882f196167d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319366"
---
# <a name="pseudotargets"></a>Pseudocíle

Pseudotarget je popisek, použijí se místo názvu souboru na řádku závislostí. Je interpretován jako soubor, který neexistuje a proto je zastaralý. NMAKE předpokládá, že že pseudotarget časové razítko je nejnovější z jejích závislých hodnot. Pokud nemá žádné závislé položky, se předpokládá, že aktuální čas. Pokud se pseudotarget používá jako cíl, jsou provedeny vždy její příkazy. Pseudotarget použít jako závislé také musí být uvedena jako cíl v jiném závislostí. Tato závislost ale není potřeba zablokování příkazy.

Názvy pseudotarget podle pravidel syntaxe názvu souboru pro cíle. Nicméně není-li název rozšíření (to znamená, že neobsahuje tečkou), může být delší než 8 znaků omezení pro názvy souborů a může mít až 256 znaků.

## <a name="see-also"></a>Viz také:

[Cíle](targets.md)
