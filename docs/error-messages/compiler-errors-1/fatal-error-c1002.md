---
title: Závažná chyba C1002 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1002
dev_langs:
- C++
helpviewer_keywords:
- C1002
ms.assetid: bd6d274a-c7b4-43af-8bf2-23c5e442aa22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f08255484b11f9f5d87fb67ac8ac7b401d4f6e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044142"
---
# <a name="fatal-error-c1002"></a>Závažná chyba C1002

kompilátoru je nedostatek místa v haldě při průchodu 2

Kompilátor nemá dostatek místa na dynamické paměti ve druhé fázi, pravděpodobně kvůli programu s příliš mnoho symbolů nebo složité výrazy.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zdrojový soubor rozdělte do několika menších souborů.

1. Výrazy rozdělte do menších dílčích výrazů.

1. Odeberte ostatní programy nebo ovladače, které využívají paměti.