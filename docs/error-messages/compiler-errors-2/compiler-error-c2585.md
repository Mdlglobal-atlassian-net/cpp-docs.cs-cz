---
title: Chyba kompilátoru C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593255"
---
# <a name="compiler-error-c2585"></a>Chyba kompilátoru C2585

explicitní převod na "typ" je nejednoznačný

Převod typu může vytvořit více než jeden výsledek.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Převod z typu třídy nebo struktury podle vícenásobnou dědičnost. Pokud typ dědí stejné základní třídy více než jednou, musíte použít funkce převodu nebo operátor rozlišení oboru (`::`) k určení zděděné třídy používané k převodu.

1. Operátor převodu a konstruktor byly definovány provádění stejný převod.