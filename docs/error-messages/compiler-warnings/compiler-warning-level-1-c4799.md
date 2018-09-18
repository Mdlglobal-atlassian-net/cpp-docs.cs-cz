---
title: Upozornění (úroveň 1) C4799 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4799
dev_langs:
- C++
helpviewer_keywords:
- C4799
ms.assetid: 8ecbd06f-c778-4371-a2fb-c690b6743ec8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d83917289e5ad76a874587894a66e163fed90a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088225"
---
# <a name="compiler-warning-level-1-c4799"></a>Kompilátor upozornění (úroveň 1) C4799

> Žádné EMMS. na konci funkce "*funkce*.

Funkci má alespoň jedna instrukce MMX, ale nemá `EMMS` instrukce. Při použití multimediálních instrukce `EMMS` instrukce nebo `_mm_empty` vnitřní by měl také použít k zrušte slovo multimediální značky na konci MMX kódu.

C4799 se může zobrazit při použití ivec.h, která udává, že kód nepoužívá správně spustit instrukci EMMS. před vrácením. Toto je false upozornění pro tyto hlavičky. Toto může vypnout definováním _SILENCE_IVEC_C4799 ivec.h. Nezapomínejte, že to bude také zabránění kompilátoru poskytuje správné upozornění tohoto typu.

Související informace naleznete v tématu [sadu instrukcí MMX společnosti Intel](../../assembler/inline/intel-s-mmx-instruction-set.md).