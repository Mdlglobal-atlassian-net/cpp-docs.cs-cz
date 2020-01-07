---
title: fcvt
ms.date: 12/16/2019
api_name:
- fcvt
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
- fcvt
helpviewer_keywords:
- fcvt function
ms.assetid: 1f748ad0-e186-400e-af8e-80d4431523d7
ms.openlocfilehash: 2e4358cbaecca29f282c32070e41771222d54067
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301181"
---
# <a name="fcvt"></a>fcvt

Název funkce specifický pro společnost Microsoft `fcvt` je zastaralý alias pro funkci [_fcvt](fcvt.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Místo toho doporučujeme použít [_fcvt](fcvt.md) nebo funkci [_fcvt_s](fcvt-s.md) s vylepšeným zabezpečením. Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).
