---
title: Závažná chyba C1002
ms.date: 11/04/2016
f1_keywords:
- C1002
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
ms.openlocfilehash: 78edf886f34665f996497abe323a0ea5d3800c2d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204929"
---
# <a name="fatal-error-c1002"></a>Závažná chyba C1002

Kompilátor má nedostatek prostoru v haldě v Pass 2.

Během druhého průchodu došlo v kompilátoru k nedostatku dynamické paměti, pravděpodobně kvůli programu s příliš velkým počtem symbolů nebo složitých výrazů.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Rozdělte zdrojový soubor na několik menších souborů.

1. Rozdělit výrazy na menší dílčí výrazy.

1. Odeberte ostatní programy nebo ovladače, které využívají paměť.
