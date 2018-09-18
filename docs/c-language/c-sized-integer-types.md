---
title: Typy Integer s nastavenou velikostí C | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 037ff61dbe1d1d42d8b0c751fcdc83f01a8dd112
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101414"
---
# <a name="c-sized-integer-types"></a>Typy Integer jazyka C s nastavenou velikostí

**Specifické pro Microsoft**

Jazyk Microsoft C obsahuje podporu pro celočíselné typy s velikostí. Je možné deklarovat 8, 16, 32- a 64bitové celočíselné proměnné pomocí __int*n* zadejte specifikátor, kde *n* velikost, v bitech celočíselné proměnné. Hodnota *n* může být 8, 16, 32 nebo 64. Následující příklad deklaruje jednu proměnnou každého ze čtyř celočíselných typů s velikostí:

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

První tři typy celočíselných typů s velikostí jsou synonyma pro typy ANSI, které mají stejnou velikost, a jsou užitečné pro psaní přenositelného kódu, který se na různých platformách chová stejně. Všimněte si, že datový typ __int8 je synonymem typu char \__int16 je synonymem typu short a \__int32 je synonymem typu int. \__Int64 typ nemá žádné odpovídající protějšek standardu ANSI.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)