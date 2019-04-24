---
title: Používání výrazu atexit
ms.date: 11/04/2016
f1_keywords:
- atexit
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
ms.openlocfilehash: 06baba59b5765f853f081b34d73be28a187730ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257995"
---
# <a name="using-atexit"></a>Používání výrazu atexit

S [atexit](../c-runtime-library/reference/atexit.md) funkce, můžete zadat funkci zpracování výstupu, který se spustí před ukončením programu. Žádné globální statické objekty inicializované před voláním **atexit** před spuštěním funkce zpracování výstupu nejsou zničeny.

## <a name="see-also"></a>Viz také:

[Další důležité informace o ukončení](../cpp/additional-termination-considerations.md)