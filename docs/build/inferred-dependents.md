---
title: Odvozené závislé objekty | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inferred dependents in NMAKE
- dependents, inferred
ms.assetid: 9303045c-69b3-4f35-bffc-19d5cd6ea3c3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 631c5631b60f0e05dd1f1541facc767f35944d3d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701477"
---
# <a name="inferred-dependents"></a>Odvozené závislé objekty

Odvozené závislé je odvozen z odvozené pravidlo a je vyhodnoceno před explicitní závislé položky. Pokud odvozené závislé není aktuální s ohledem na cíli, vyvolá NMAKE bloku příkazů pro závislost. Pokud odvozené závislé neexistuje nebo není aktuální s ohledem na své vlastní závislé objekty, NMAKE nejprve aktualizuje odvozené závislé. Další informace o odvozené závislé objekty, najdete v části [pravidla odvozování](../build/inference-rules.md).

## <a name="see-also"></a>Viz také

[Závislé prvky](../build/dependents.md)