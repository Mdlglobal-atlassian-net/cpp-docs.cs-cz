---
title: Kompilátor upozornění (úroveň 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 6e1f2a2396447038f6a117f66d4002bea7fd7486
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513669"
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilátor upozornění (úroveň 1) C4041

limit kompilátoru: ukončuje se výstup prohlížeče

Informace o prohlížeči překročil limit kompilátoru.

Toto upozornění může být způsobeno kompilaci [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně lokálních proměnných).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Kompilovat s /Fr (informace o prohlížeči bez lokální proměnné).

1. Zakážete výstup prohlížeče (kompilace bez /FR nebo /Fr).