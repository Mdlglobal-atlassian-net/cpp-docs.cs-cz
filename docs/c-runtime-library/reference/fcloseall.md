---
title: fcloseall
ms.date: 12/16/2019
api_name:
- fcloseall
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
- fcloseall
helpviewer_keywords:
- fcloseall function
ms.assetid: 4f14acde-5bc5-43da-a709-7a3c559df3cf
ms.openlocfilehash: 1594e510239949062fde8bf3a8fb036b4cafa16f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299517"
---
# <a name="fcloseall"></a>fcloseall

Název funkce specifický pro společnost Microsoft `fcloseall` je zastaralý alias pro funkci [_fcloseall](fclose-fcloseall.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Doporučujeme místo toho použít [_fcloseall](fclose-fcloseall.md) . Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
