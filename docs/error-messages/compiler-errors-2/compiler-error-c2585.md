---
title: Chyba kompilátoru C2585 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2585
dev_langs:
- C++
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ec7b1e9c1e5e7894740cc80f9c030fa1ee26ec0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028841"
---
# <a name="compiler-error-c2585"></a>Chyba kompilátoru C2585

explicitní převod na "typ" je nejednoznačný

Převod typu může vytvořit více než jeden výsledek.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Převod z typu třídy nebo struktury podle vícenásobnou dědičnost. Pokud typ dědí stejné základní třídy více než jednou, musíte použít funkce převodu nebo operátor rozlišení oboru (`::`) k určení zděděné třídy používané k převodu.

1. Operátor převodu a konstruktor byly definovány provádění stejný převod.