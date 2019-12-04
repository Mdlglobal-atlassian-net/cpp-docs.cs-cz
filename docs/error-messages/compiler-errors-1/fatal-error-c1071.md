---
title: Závažná chyba C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747407"
---
# <a name="fatal-error-c1071"></a>Závažná chyba C1071

v komentáři se našel neočekávaný konec souboru.

Kompilátor dosáhl konce souboru při skenování komentáře.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Chybí ukončovací znak komentáře (*/).

1. Po komentáři na posledním řádku zdrojového souboru chybí znak nového řádku.

Následující ukázka generuje C1071:

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
