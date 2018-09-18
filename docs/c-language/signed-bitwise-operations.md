---
title: Podepsané bitové operace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- bitwise operations
- signed bitwise operations
ms.assetid: 1e5cf65b-ee32-41a0-a5c2-82c1854091f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 184fd5a0e6c12cb58e9fed759459e7b8172896f8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038292"
---
# <a name="signed-bitwise-operations"></a>Podepsané bitové operace

**ANSI 3.3** výsledky bitových operací s celými čísly se znaménkem

Bitové operace s celými čísly se znaménkem fungují stejně jako bitové operace s celými čísly bez znaménka. Například `-16 & 99` může být vyjádřena v binárním souboru jako

```
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Výsledkem bitové operace AND je 96.

## <a name="see-also"></a>Viz také

[Celá čísla](../c-language/integers.md)