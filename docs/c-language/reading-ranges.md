---
title: Čtení rozsahů
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: 86bb24647084d8bdc452960bab631587c2413276
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343152"
---
# <a name="reading-ranges"></a>Čtení rozsahů

**ANSI 4.9.6.2** interpretace znaku pomlčky (-), který není prvním ani posledním znakem v seznamu % [převodu ve `fscanf` – funkce

Následující řádek

```
fscanf( fileptr, "%[A-Z]", strptr);
```

načte libovolný počet znaků v rozsahu A – Z do řetězce ke kterému `strptr` body.

## <a name="see-also"></a>Viz také:

[Funkce knihovny](../c-language/library-functions.md)
