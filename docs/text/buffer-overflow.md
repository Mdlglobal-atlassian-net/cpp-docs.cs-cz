---
title: Přetečení vyrovnávací paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9bb362be360986371200c8cde292b3fff5acd7cd
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40020184"
---
# <a name="buffer-overflow"></a>Přetečení vyrovnávací paměti
Různé velikosti znaků může způsobovat problémy při uvádění znaků do vyrovnávací paměti. Vezměte v úvahu následující kód, který kopíruje znaků z řetězce, `sz`, do vyrovnávací paměti, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 Otázka: byl zkopírován poslední bajt úvodní bajt? Tímto problém nevyřeší, protože to může potenciálně přetečení vyrovnávací paměti:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` Volání se pokusí provést správnou věc – úplné znak zkopírovat, ať už jde o 1 nebo 2 bajty. Ale nebere v úvahu, že poslední znak zkopírovat nevešel vyrovnávací paměti Pokud znak je 2 bajty široké. Správné řešení je:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Tento kód testuje přetečení vyrovnávací paměti je možný ve smyčce otestovat, pomocí `_mbclen` otestovat velikost aktuální znak, který ukazuje `sz`. Tím, že volání `_mbsnbcpy` funkce, můžete nahradit kód v **při** smyčky s jediný řádek kódu. Příklad:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)