---
title: Kompilátor upozornění (úroveň 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 8c5c15105581602566116d3ed82b89a6337435c9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50627627"
---
# <a name="compiler-warning-level-3-c4278"></a>Kompilátor upozornění (úroveň 3) C4278

> "*identifikátor*': identifikátor v knihovně typů '*vyrovnávací paměti tlb*" už je makro; použijte kvalifikátor "přejmenovat"

Při použití [#import](../../preprocessor/hash-import-directive-cpp.md), identifikátor v knihovně typů, který importujete se pokouší o deklaraci identifikátoru *identifikátor*. To je však již symbol platný.

Použití `#import` **přejmenovat** atribut přiřadit alias symbolů v knihovně typů.