---
title: Upozornění (úroveň 3) C4278 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4278
dev_langs:
- C++
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f63337de2e14b1cb0f9d854df962ab2aa9c8014e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205778"
---
# <a name="compiler-warning-level-3-c4278"></a>Kompilátor upozornění (úroveň 3) C4278

> "*identifikátor*': identifikátor v knihovně typů '*vyrovnávací paměti tlb*" už je makro; použijte kvalifikátor "přejmenovat"

Při použití [#import](../../preprocessor/hash-import-directive-cpp.md), identifikátor v knihovně typů, který importujete se pokouší o deklaraci identifikátoru *identifikátor*. To je však již symbol platný.

Použití `#import` **přejmenovat** atribut přiřadit alias symbolů v knihovně typů.