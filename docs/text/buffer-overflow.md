---
title: Přetečení vyrovnávací paměti
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 97488f3023481c20599e8cf5201fbce68dd23516
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566497"
---
# <a name="buffer-overflow"></a>Přetečení vyrovnávací paměti

Různé velikosti znaků může způsobovat problémy při uvádění znaků do vyrovnávací paměti. Vezměte v úvahu následující kód, který kopíruje znaků z řetězce, `sz`, do vyrovnávací paměti, `rgch`:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

Otázka: byl zkopírován poslední bajt úvodní bajt? Tímto problém nevyřeší, protože to může potenciálně přetečení vyrovnávací paměti:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy` Volání se pokusí provést správnou věc – úplné znak zkopírovat, ať už jde o 1 nebo 2 bajty. Ale nebere v úvahu, že poslední znak zkopírovat nevešel vyrovnávací paměti Pokud znak je 2 bajty široké. Správné řešení je:

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Tento kód testuje přetečení vyrovnávací paměti je možný ve smyčce otestovat, pomocí `_mbclen` otestovat velikost aktuální znak, který ukazuje `sz`. Tím, že volání `_mbsnbcpy` funkce, můžete nahradit kód v **při** smyčky s jediný řádek kódu. Příklad:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Viz také

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)