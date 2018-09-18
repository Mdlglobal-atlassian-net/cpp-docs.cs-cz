---
title: Upozornění (úroveň 1) C4041 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4041
dev_langs:
- C++
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff2c8066557e420ecd7de561d7731b7be733315
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46085781"
---
# <a name="compiler-warning-level-1-c4041"></a>Kompilátor upozornění (úroveň 1) C4041

limit kompilátoru: ukončuje se výstup prohlížeče

Informace o prohlížeči překročil limit kompilátoru.

Toto upozornění může být způsobeno kompilaci [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (informace o prohlížeči včetně lokálních proměnných).

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Kompilovat s /Fr (informace o prohlížeči bez lokální proměnné).

1. Zakážete výstup prohlížeče (kompilace bez /FR nebo /Fr).