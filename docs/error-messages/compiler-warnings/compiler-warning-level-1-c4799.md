---
title: Kompilátor upozornění (úroveň 1) C4799
ms.date: 11/04/2016
f1_keywords:
- C4799
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
ms.openlocfilehash: 475451b47d461e7ea1428eb715a876fb023694d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152213"
---
# <a name="compiler-warning-level-1-c4799"></a>Kompilátor upozornění (úroveň 1) C4799

> Žádné EMMS. na konci funkce "*funkce*.

Funkci má alespoň jedna instrukce MMX, ale nemá `EMMS` instrukce. Při použití multimediálních instrukce `EMMS` instrukce nebo `_mm_empty` vnitřní by měl také použít k zrušte slovo multimediální značky na konci MMX kódu.

C4799 se může zobrazit při použití ivec.h, která udává, že kód nepoužívá správně spustit instrukci EMMS. před vrácením. Toto je false upozornění pro tyto hlavičky. Toto může vypnout definováním _SILENCE_IVEC_C4799 ivec.h. Nezapomínejte, že to bude také zabránění kompilátoru poskytuje správné upozornění tohoto typu.

Související informace naleznete v tématu [sadu instrukcí MMX společnosti Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).