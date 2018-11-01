---
title: Závažná chyba C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 0588da99994be547742cc530ba435002a2d73359
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640502"
---
# <a name="fatal-error-c1002"></a>Závažná chyba C1002

kompilátoru je nedostatek místa v haldě při průchodu 2

Kompilátor nemá dostatek místa na dynamické paměti ve druhé fázi, pravděpodobně kvůli programu s příliš mnoho symbolů nebo složité výrazy.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zdrojový soubor rozdělte do několika menších souborů.

1. Výrazy rozdělte do menších dílčích výrazů.

1. Odeberte ostatní programy nebo ovladače, které využívají paměti.