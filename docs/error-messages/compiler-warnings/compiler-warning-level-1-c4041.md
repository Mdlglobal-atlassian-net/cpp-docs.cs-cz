---
title: Kompilátor upozornění (úroveň 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: 6e1f2a2396447038f6a117f66d4002bea7fd7486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151315"
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilátor upozornění (úroveň 1) C4041

limit kompilátoru: ukončuje se výstup prohlížeče

Informace o prohlížeči překročil limit kompilátoru.

Toto upozornění může být způsobeno kompilaci [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně lokálních proměnných).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Kompilovat s /Fr (informace o prohlížeči bez lokální proměnné).

1. Zakážete výstup prohlížeče (kompilace bez /FR nebo /Fr).