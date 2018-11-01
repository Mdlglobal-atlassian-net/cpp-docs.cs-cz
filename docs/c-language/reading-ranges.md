---
title: Čtení rozsahů
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: b5c6a6baf43b8786fbd0301e4b89ea856d839606
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604102"
---
# <a name="reading-ranges"></a>Čtení rozsahů

**ANSI 4.9.6.2** interpretace znaku pomlčky (-), který není prvním ani posledním znakem v seznamu % [převodu ve `fscanf` – funkce

Následující řádek

```
fscanf( fileptr, "%[A-Z]", strptr);
```

načte libovolný počet znaků v rozsahu A – Z do řetězce ke kterému `strptr` body.

## <a name="see-also"></a>Viz také

[Funkce knihovny](../c-language/library-functions.md)