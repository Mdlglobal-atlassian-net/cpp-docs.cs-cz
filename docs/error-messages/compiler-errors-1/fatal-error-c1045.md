---
title: Závažná chyba C1045
ms.date: 11/04/2016
f1_keywords:
- C1045
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
ms.openlocfilehash: 2d1b1bb626e420f972993d73063e798b16e447a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204593"
---
# <a name="fatal-error-c1045"></a>Závažná chyba C1045

limit kompilátoru: specifikace propojení jsou vnořené moc hluboko.

Vnořené externí typy překračují limit kompilátoru. Vnořené externí typy jsou povoleny s typem vnější propojení, například `extern` "C++". Pokud chcete chybu vyřešit, snižte počet vnořených externích typů.
