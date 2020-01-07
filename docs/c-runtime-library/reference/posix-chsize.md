---
title: chsize
ms.date: 12/16/2019
api_name:
- chsize
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
- chsize
helpviewer_keywords:
- chsize function
ms.assetid: f94d62f6-b539-4cbf-bf99-b81d081b4216
ms.openlocfilehash: c3a239ec67f01f10adcee20c5c3170461e436f6e
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300999"
---
# <a name="chsize"></a>chsize

Název funkce specifický pro společnost Microsoft `chsize` je zastaralý alias pro funkci [_chsize](chsize.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Místo toho doporučujeme použít [_chsize](chsize.md) nebo funkci [_chsize_s](chsize-s.md) s vylepšeným zabezpečením. Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
