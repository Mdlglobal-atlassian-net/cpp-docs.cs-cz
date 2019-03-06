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
ms.openlocfilehash: 34b2b2f0d54a6e11bdfd6e818eb08d01721d80e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414833"
---
# <a name="pseudotargets"></a>Pseudocíle

Pseudotarget je popisek, použijí se místo názvu souboru na řádku závislostí. Je interpretován jako soubor, který neexistuje a proto je zastaralý. NMAKE předpokládá, že že pseudotarget časové razítko je nejnovější z jejích závislých hodnot. Pokud nemá žádné závislé položky, se předpokládá, že aktuální čas. Pokud se pseudotarget používá jako cíl, jsou provedeny vždy její příkazy. Pseudotarget použít jako závislé také musí být uvedena jako cíl v jiném závislostí. Tato závislost ale není potřeba zablokování příkazy.

Názvy pseudotarget podle pravidel syntaxe názvu souboru pro cíle. Nicméně není-li název rozšíření (to znamená, že neobsahuje tečkou), může být delší než 8 znaků omezení pro názvy souborů a může mít až 256 znaků.

## <a name="see-also"></a>Viz také:

[Cíle](../build/targets.md)
