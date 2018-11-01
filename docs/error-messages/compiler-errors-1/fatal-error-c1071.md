---
title: Závažná chyba C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 8fe6b0f3bb1253f72c97f29070ba81cdbdf80508
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506701"
---
# <a name="fatal-error-c1071"></a>Závažná chyba C1071

Neočekávaný konec souboru v komentáři se našel

Kompilátor bylo dosaženo konce souboru při hledání komentář.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Chybí ukončovací znak komentář (* /).

1. Chybí znak nového řádku za komentář na posledním řádku zdrojového souboru.

Následující ukázka generuje C1071:

```
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```