---
title: Rozsah hodnot typu char
ms.date: 11/04/2016
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
ms.openlocfilehash: 8cb2609aca910056b5243fddc868710581e576e7
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480909"
---
# <a name="range-of-char-values"></a>Rozsah hodnot typu char

**ANSI 3.2.1.1** Zda "prostý" **char** má stejný rozsah hodnot jako **podepsané char** nebo **nepodepsané char**

Všechny podepsané hodnoty znaků jsou v rozsahu od -128 do 127. Všechny hodnoty znaků bez znaménka mají rozsah od 0 do 255.

Možnost [`/J`](../build/reference/j-default-char-type-is-unsigned.md) kompilátoru změní výchozí typ **znaku** z **podepsaného znaku** na **nepodepsaný znak**.

## <a name="see-also"></a>Viz také

[Znaky](../c-language/characters.md)
