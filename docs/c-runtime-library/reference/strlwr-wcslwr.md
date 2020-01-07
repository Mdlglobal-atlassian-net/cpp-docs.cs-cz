---
title: strlwr, wcslwr
ms.date: 12/16/2019
api_name:
- strlwr
- wcslwr
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
- wcslwr
- strlwr
helpviewer_keywords:
- strlwr function
- wcslwr function
ms.assetid: b9274824-4365-4674-b656-823c89653656
ms.openlocfilehash: ff730d6bea6619c50fefb407a7a69c50e1a06af0
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301077"
---
# <a name="strlwr-wcslwr"></a>strlwr, wcslwr

Názvy funkcí specifických pro společnost Microsoft `strlwr` a `wcslwr` jsou zastaralé aliasy pro [_strlwr a _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) funkce. Ve výchozím nastavení generují [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Názvy jsou zastaralé, protože nenásledují standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce se ale pořád podporují.

Doporučujeme místo toho použít [_strlwr nebo _wcslwr](strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) nebo [_strlwr_s a _wcslwr_s](strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md) funkce zabezpečení vylepšené zabezpečením. Nebo můžete tyto názvy funkcí i nadále používat a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
