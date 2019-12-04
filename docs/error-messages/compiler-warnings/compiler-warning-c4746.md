---
title: Upozornění kompilátoru C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 9e761deb1b8c1b00e025f49775a845d07985fd2c
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810579"
---
# <a name="compiler-warning-c4746"></a>Upozornění kompilátoru C4746

nestálý přístup k výrazu\<Expression > podléhá nastavení/volatile: [ISO&#124;MS]. Zvažte použití vnitřních funkcí __iso_volatile_load/Store.

C4746 je generována vždy, když je k dispozici volatile proměnné přímo. Je určena k tomu, aby usnadnila vývojářům identifikovat umístění kódu, která jsou ovlivněná konkrétním nestálým modelem (který lze ovládat pomocí možnosti kompilátoru [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) ). Konkrétně může být užitečné při hledání hardwarových bariér generovaných kompilátorem při použití/volatile: MS.

Vnitřní objekty __iso_volatile_load/Store lze použít k explicitnímu přístupu k nestálé paměti, aniž by to ovlivnil model volatile. Pomocí těchto vnitřních objektů se C4746 neaktivují.

Toto upozornění je ve výchozím nastavení vypnuté. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .