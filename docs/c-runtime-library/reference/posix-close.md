---
title: close
ms.date: 12/16/2019
api_name:
- close
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- close
helpviewer_keywords:
- close function
ms.assetid: c79689f4-9c86-4a4a-a256-d22e3498f55d
ms.openlocfilehash: 1d3c02e3e2e015d0560b9ca70243f35c9f4a0888
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301220"
---
# <a name="close"></a>close

Název funkce POSIX `close`, který implementuje Microsoft, je zastaralý alias pro funkci [_close](close.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Doporučujeme místo toho použít [_close](close.md) . Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
