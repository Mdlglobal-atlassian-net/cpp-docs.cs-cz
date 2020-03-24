---
title: Upozornění kompilátoru (úroveň 1) C4729
ms.date: 11/04/2016
f1_keywords:
- C4729
helpviewer_keywords:
- C4729
ms.assetid: 36a0151f-f258-48d9-9444-ae6d41ff70a4
ms.openlocfilehash: e78606f117251fa8ab1f08f2cef280a266309c32
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185825"
---
# <a name="compiler-warning-level-1-c4729"></a>Upozornění kompilátoru (úroveň 1) C4729

funkce je moc velká pro upozornění založená na grafu toku.

Toto upozornění je vygenerováno, pokud je funkce příliš velká pro zkompilování s spolehlivou kontrolou pro situace, které by vygenerovala upozornění. Toto upozornění se generuje jenom v případě, že se použila možnost kompilátoru [/od](../../build/reference/od-disable-debug.md) .

Chcete-li toto upozornění vyřešit, předělte funkci na menší funkce.
