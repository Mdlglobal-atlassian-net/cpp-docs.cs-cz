---
title: execle
ms.date: 12/16/2019
api_name:
- execle
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
- execle
helpviewer_keywords:
- execle function
ms.assetid: 5985b615-fe90-4d1c-9c1d-13ec87c8e306
ms.openlocfilehash: 1d97d847ae16c0f0224eca9fba42ad1ab5452b10
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299777"
---
# <a name="execle"></a>execle

Název funkce POSIX `execle`, který implementuje Microsoft, je zastaralý alias pro funkci [_execle](execle-wexecle.md) . Ve výchozím nastavení vygeneruje [Upozornění kompilátoru (úroveň 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md). Název je zastaralý, protože nedodržuje standardní pravidla jazyka C pro názvy specifické pro implementaci. Funkce je však stále podporována.

Doporučujeme místo toho použít [_execle](execle-wexecle.md) . Nebo můžete i nadále používat tento název funkce a zakázat upozornění. Další informace najdete v tématu vypnutí názvů funkcí [Upozornění](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning) a [funkce POSIX](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).
