---
title: mktemp
ms.date: 12/16/2019
api_name:
- mktemp
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
- mktemp
helpviewer_keywords:
- mktemp function
ms.assetid: b58cba60-034f-4e63-b312-ccbcd489d0a7
ms.openlocfilehash: c9efd79111c000764561ba415db79a13a34c46fe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301012"
---
# <a name="mktemp"></a>mktemp

Název funkce specifický pro společnost Microsoft `mktemp` je zastaralý alias pro funkci [_mktemp](mktemp-wmktemp.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Místo toho doporučujeme použít [_mktemp](mktemp-wmktemp.md) nebo funkci [_mktemp_s](mktemp-s-wmktemp-s.md) s vylepšeným zabezpečením. Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
