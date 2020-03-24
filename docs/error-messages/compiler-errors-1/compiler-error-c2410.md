---
title: Chyba kompilátoru C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: e4d30ff0fbca7428fb1dcf252bcad50bd53488d7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205689"
---
# <a name="compiler-error-c2410"></a>Chyba kompilátoru C2410

' identifier ': nejednoznačný název členu v kontextu '

Identifikátor je členem více než jedné struktury nebo sjednocení v tomto kontextu.

Pro operand, který způsobil chybu, použijte specifikátor struktury nebo sjednocení. Specifikátor struktury nebo sjednocení je identifikátor typu `struct` nebo `union` (`typedef` název nebo proměnná stejného typu jako odkazovaná struktura nebo sjednocení). Specifikátorem musí být levý operand prvního operátoru výběru členů (.), aby se mohl použít operand.
