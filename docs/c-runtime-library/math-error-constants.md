---
title: Konstanty matematické chyby
ms.date: 11/04/2016
f1_keywords:
- _PLOSS
- _UNDERFLOW
- _TLOSS
- _SING
- _DOMAIN
- _OVERFLOW
helpviewer_keywords:
- _TLOSS constant
- _SING constant
- PLOSS constant
- UNDERFLOW constant
- _UNDERFLOW constant
- _OVERFLOW constant
- DOMAIN constant
- OVERFLOW constant
- TLOSS constant
- SING constant
- _DOMAIN constant
- _PLOSS constant
- math error constants
ms.assetid: 4be933a6-674e-45a5-8ac9-090023542f5b
ms.openlocfilehash: f51d9a3a28118d922f81a44e31c9abc610645f13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524986"
---
# <a name="math-error-constants"></a>Konstanty matematické chyby

## <a name="syntax"></a>Syntaxe

```

#include <math.h>
```

## <a name="remarks"></a>Poznámky

Matematické rutiny knihovny run-time může generovat konstanty matematické chyby.

Tyto chyby, následujícím způsobem popsané odpovídají typy výjimek, které jsou definované v MATEMATICE. H a jsou vrácené `_matherr` fungovat v případě, že dojde k chybě matematické.

|Konstanta|Význam|
|--------------|-------------|
|`_DOMAIN`|Argument funkce je mimo doménu funkce.|
|`_OVERFLOW`|Výsledek je příliš velký, aby se dala vyjádřit v návratovém typu funkce.|
|`_PLOSS`|Došlo k částečné ztrátě významu.|
|`_SING`|Argument singularity: argument funkce má neplatnou hodnotu. (Například, hodnota 0 předána funkci, která vyžaduje nenulovou hodnotu.)|
|`_TLOSS`|Celkový počet ke ztrátě významu došlo k chybě.|
|`_UNDERFLOW`|Výsledek je příliš malá, aby se dala vyjádřit.|

## <a name="see-also"></a>Viz také

[_matherr](../c-runtime-library/reference/matherr.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)