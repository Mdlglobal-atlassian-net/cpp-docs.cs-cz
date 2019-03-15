---
title: Odvozené závislé objekty
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: 2382dec960ef93fc2f73987ad27b4670768a68cc
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823109"
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty

Odvozené závislé je odvozen z odvozené pravidlo a je vyhodnoceno před explicitní závislé položky. Pokud odvozené závislé není aktuální s ohledem na cíli, vyvolá NMAKE bloku příkazů pro závislost. Pokud odvozené závislé neexistuje nebo není aktuální s ohledem na své vlastní závislé objekty, NMAKE nejprve aktualizuje odvozené závislé. Další informace o odvozené závislé objekty, najdete v části [pravidla odvozování](inference-rules.md).

## <a name="see-also"></a>Viz také:

[Závislé prvky](dependents.md)
