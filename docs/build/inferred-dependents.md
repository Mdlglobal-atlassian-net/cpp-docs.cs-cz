---
title: Odvozené závislé objekty
ms.date: 11/04/2016
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
ms.openlocfilehash: d4d12d0ab686c604ce0d4495df89ec62c6160ebe
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414145"
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty

Odvozené závislé je odvozen z odvozené pravidlo a je vyhodnoceno před explicitní závislé položky. Pokud odvozené závislé není aktuální s ohledem na cíli, vyvolá NMAKE bloku příkazů pro závislost. Pokud odvozené závislé neexistuje nebo není aktuální s ohledem na své vlastní závislé objekty, NMAKE nejprve aktualizuje odvozené závislé. Další informace o odvozené závislé objekty, najdete v části [pravidla odvozování](../build/inference-rules.md).

## <a name="see-also"></a>Viz také:

[Závislé prvky](../build/dependents.md)
