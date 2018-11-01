---
title: Odvozené závislé objekty
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 958a33c29be0d68fee1044fff1d81235ea9370c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641373"
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty

Odvozené závislé je odvozen z odvozené pravidlo a je vyhodnoceno před explicitní závislé položky. Pokud odvozené závislé není aktuální s ohledem na cíli, vyvolá NMAKE bloku příkazů pro závislost. Pokud odvozené závislé neexistuje nebo není aktuální s ohledem na své vlastní závislé objekty, NMAKE nejprve aktualizuje odvozené závislé. Další informace o odvozené závislé objekty, najdete v části [pravidla odvozování](../build/inference-rules.md).

## <a name="see-also"></a>Viz také

[Závislé prvky](../build/dependents.md)