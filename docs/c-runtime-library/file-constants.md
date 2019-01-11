---
title: Konstanty souboru
ms.date: 11/04/2016
f1_keywords:
- _O_EXCL
- _O_RDWR
- _O_APPEND
- _O_RDONLY
- _O_TRUNC
- _O_CREAT
- _O_WRONLY
helpviewer_keywords:
- _O_RDWR constant
- O_EXCL constant
- O_RDWR constant
- O_WRONLY constant
- O_APPEND constant
- O_CREAT constant
- _O_CREAT constant
- _O_APPEND constant
- _O_EXCL constant
- O_TRUNC constant
- _O_RDONLY constant
- _O_TRUNC constant
- O_RDONLY constant
- _O_WRONLY constant
ms.assetid: c8fa5548-9ac2-4217-801d-eb45e86f2fa4
ms.openlocfilehash: 2dc473db50b1835d4e1495ce255c0a826563b70a
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220436"
---
# <a name="file-constants"></a>Konstanty souboru

## <a name="syntax"></a>Syntaxe

```
#include <fcntl.h>
```

## <a name="remarks"></a>Poznámky

Celočíselný výraz formátovaných z jednoho nebo více z následujících konstant Určuje typ čtení nebo zápisu operace povolena. Je vytvořen kombinací jeden nebo více konstant s konstanty režimu překladu.

Konstanty souboru jsou následující:

|Konstanta|Popis|
|-|-|
| `_O_APPEND`  | Přemístí ukazatel na soubor na konec souboru před každou operaci zápisu.  |
| `_O_CREAT`  | Vytvoří a otevře se nový soubor pro zápis; To nemá vliv, pokud souboru určeném *filename* existuje.  |
| `_O_EXCL`  | Vrací chybovou hodnotu, pokud souboru určeném *filename* existuje. Platí jenom při použití s `_O_CREAT`.  |
| `_O_RDONLY`  | Otevře se soubor jen pro čtení Pokud je zadaný tento příznak, ani `_O_RDWR` ani `_O_WRONLY` mohou být zadány.  |
| `_O_RDWR`  | Otevře soubor pro čtení i zápis; Pokud je zadaný tento příznak, ani `_O_RDONLY` ani `_O_WRONLY` mohou být zadány.  |
| `_O_TRUNC`  | Otevře a zkrátí existující soubor na nulu length; soubor musí mít oprávnění k zápisu. Obsah souboru jsou zničeny. Pokud je zadaný tento příznak, nelze zadat `_O_RDONLY`.  |
| `_O_WRONLY`  | Otevře soubor pro zápis. Pokud je zadaný tento příznak, ani `_O_RDONLY` ani `_O_RDWR` mohou být zadány.  |

## <a name="see-also"></a>Viz také

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[Globální konstanty](../c-runtime-library/global-constants.md)
