---
title: umask
ms.date: 12/16/2019
api_name:
- umask
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
- umask
helpviewer_keywords:
- umask function
ms.assetid: d2f697fc-08d5-4b70-9dd5-df3f5bb8b754
ms.openlocfilehash: e22832b7c4b9e9f7af0a6e98955a15b783c6931f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301103"
---
# <a name="umask"></a>umask

Název funkce POSIX `umask`, který implementuje Microsoft, je zastaralý alias pro funkci [_umask](umask.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Místo toho doporučujeme použít [_umask](umask.md) nebo [_umask_s](umask-s.md) funkci vylepšené zabezpečení. Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
