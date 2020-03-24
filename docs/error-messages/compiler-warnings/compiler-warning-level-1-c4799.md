---
title: Upozornění kompilátoru (úroveň 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: ec92da425718cd5ddc579d1d733a0bc4e56dc04a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175100"
---
# <a name="compiler-warning-level-1-c4799"></a>Upozornění kompilátoru (úroveň 1) C4799

> Žádné žádnou Emms na konci funkce*Function*

Funkce má alespoň jednu instrukci MMX, ale nemá instrukci `EMMS`. Při použití multimediální instrukce by se měla použít taky `EMMS` instrukci nebo `_mm_empty` vnitřní, aby se na konci kódu MMX vymazalo slovo multimediální značky.

Můžete získat C4799 při použití ivec. h, což značí, že kód nepoužívá správné spuštění instrukce žádnou Emms před vrácením. Toto je falešně výstražné upozornění pro tyto hlavičky. Je možné je vypnout definováním _SILENCE_IVEC_C4799 v IVEC. h. Uvědomte si však, že se tím také zabrání kompilátoru v poskytování správných upozornění tohoto typu.

Související informace najdete v tématu [instrukční sada MMX Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).
