---
title: Bitová pole | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- bitfields
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a7451ea6afee81cc296fb091705bde48041ef5d1
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722485"
---
# <a name="bitfields"></a>Bitová pole

Struktura bitová pole jsou omezené na 64 bitů a nemůže být typu int, unsigned int, int64 nebo bez znaménka int64 podepsané. Bitová pole, které překračují hranice typu přeskočí bits zarovnáním zarovnání dalšího typu. Například bitová pole celé číslo nemusí napříč autonomního 32-bit.

## <a name="see-also"></a>Viz také

[Typy a úložiště](../build/types-and-storage.md)