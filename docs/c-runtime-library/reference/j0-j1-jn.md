---
title: j0, j1, jn
ms.date: 12/16/2019
api_name:
- jn
- j0
- j1
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
- jn
- j1
- j0
helpviewer_keywords:
- jn function
- j1 function
- j0 function
ms.assetid: ec8a9512-aacb-423c-a845-fc8927e6e21d
ms.openlocfilehash: a3dc02c1e85a57be119899a962d284d923cb42d8
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299231"
---
# <a name="j0-j1-jn"></a>j0, j1, jn

Názvy funkcí POSIX `j0`, `j1`a `jn` společnosti Microsoft implementovaného jsou nepoužívané aliasy pro funkce [_j0, _j1 a _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Ve výchozím nastavení generují [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Názvy jsou zastaralé, protože nenásledují standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce se ale pořád podporují.

Místo toho doporučujeme použít [_j0, _j1 a _jn](bessel-functions-j0-j1-jn-y0-y1-yn.md) . Nebo můžete tyto názvy funkcí i nadále používat a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
