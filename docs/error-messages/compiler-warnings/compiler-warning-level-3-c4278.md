---
title: Upozornění kompilátoru (úroveň 3) C4278
ms.date: 08/27/2018
f1_keywords:
- C4278
helpviewer_keywords:
- C4278
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
ms.openlocfilehash: 7994ae05d6cb16b5ddc9775b1044de7f3a22d542
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174229"
---
# <a name="compiler-warning-level-3-c4278"></a>Upozornění kompilátoru (úroveň 3) C4278

> '*Identifier*': identifikátor v knihovně typů '*TLB*' je již makro; použít kvalifikátor rename

Při použití [#import](../../preprocessor/hash-import-directive-cpp.md)se identifikátor v knihovně TypeLib, který importujete, pokouší deklarovat *identifikátor*identifikátoru. Toto je však již platný symbol.

Pomocí atributu `#import` **Přejmenovat** přiřaďte alias k symbolu v knihovně typů.
