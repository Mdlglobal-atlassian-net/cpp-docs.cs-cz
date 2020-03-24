---
title: Upozornění kompilátoru C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 7179e2e6d4ec44355e7338ffc4e9ba36f5de47e4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165103"
---
# <a name="compiler-warning-c4746"></a>Upozornění kompilátoru C4746

nestálý přístup k výrazu\<Expression > podléhá nastavení/volatile: [ISO&#124;MS]. Zvažte použití vnitřních funkcí __iso_volatile_load/Store.

C4746 je generována vždy, když je k dispozici volatile proměnné přímo. Je určena k tomu, aby usnadnila vývojářům identifikovat umístění kódu, která jsou ovlivněná konkrétním nestálým modelem (který lze ovládat pomocí možnosti kompilátoru [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) ). Konkrétně může být užitečné při hledání hardwarových bariér generovaných kompilátorem při použití/volatile: MS.

Vnitřní objekty __iso_volatile_load/Store lze použít k explicitnímu přístupu k nestálé paměti, aniž by to ovlivnil model volatile. Pomocí těchto vnitřních objektů se C4746 neaktivují.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .
