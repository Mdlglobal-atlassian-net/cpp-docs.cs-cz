---
title: Typy Integer jazyka C s nastavenou velikostí
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 136065466d3adb4017cf18f2baf8c3387ffbd035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313295"
---
# <a name="c-sized-integer-types"></a>Typy Integer jazyka C s nastavenou velikostí

**Specifické pro Microsoft**

Jazyk Microsoft C obsahuje podporu pro celočíselné typy s velikostí. Pomocí specifikátoru typu __int*n* můžete deklarovat 8, 16, 32 nebo 64 celočíselných proměnných, kde *n* je velikost celočíselné proměnné v bitech. Hodnota *n* může být 8, 16, 32 nebo 64. Následující příklad deklaruje jednu proměnnou každého ze čtyř celočíselných typů s velikostí:

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

První tři typy celočíselných typů s velikostí jsou synonyma pro typy ANSI, které mají stejnou velikost, a jsou užitečné pro psaní přenositelného kódu, který se na různých platformách chová stejně. Všimněte si, že __int8 datový typ je synonymum typu char, \__int16 je synonymum typu short a \__int32 je synonymum typu int. Typ \__int64 nemá žádný ekvivalentní protějšek ANSI.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Úložiště základních typů](../c-language/storage-of-basic-types.md)
