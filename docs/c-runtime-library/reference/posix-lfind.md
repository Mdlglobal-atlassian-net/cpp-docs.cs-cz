---
title: lfind
ms.date: 12/16/2019
api_name:
- lfind
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
- lfind
helpviewer_keywords:
- lfind function
ms.assetid: 2528e787-94b6-4740-8a8d-6efc276d1f42
ms.openlocfilehash: 7a1ac69bbebfea45345c7dae17b18f02b84228cd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300908"
---
# <a name="lfind"></a>lfind

Název funkce POSIX `lfind`, který implementuje Microsoft, je zastaralý alias pro funkci [_lfind](lfind.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Místo toho doporučujeme použít [_lfind](lfind.md) nebo [_lfind_s](lfind-s.md) funkci vylepšené zabezpečení. Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
