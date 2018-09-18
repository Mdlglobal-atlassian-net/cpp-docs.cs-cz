---
title: Rozsah hodnot typu char | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 15ae9781-ec21-4333-bba8-6d2383bbf7f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b45d828cecb5908742a193c8836bc4b565a6498
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110689"
---
# <a name="range-of-char-values"></a>Rozsah hodnot typu char

**ANSI 3.2.1.1** zda "prostý" **char** má stejný rozsah hodnot jako **podepsané char** nebo `unsigned char`

Všechny podepsané znak hodnoty v rozmezí -128 až 127. Všechny hodnoty znaků bez znaménka mají rozsah od 0 do 255.

Možnost kompilátoru /J změní výchozí z **podepsané** k `unsigned`.

## <a name="see-also"></a>Viz také

[Znaky](../c-language/characters.md)