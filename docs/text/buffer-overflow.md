---
title: Přetečení vyrovnávací paměti | Microsoft Docs
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
ms.openlocfilehash: 13d01460e7ed9cb95d92303d82ea136803737331
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="buffer-overflow"></a>Přetečení vyrovnávací paměti
Různé velikosti znaků může způsobit problémy, když vložíte znaků do vyrovnávací paměti. Vezměte v úvahu následující kód, který kopíruje znaků z řetězce, `sz`, do vyrovnávací paměti, `rgch`:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 Otázka se: byl poslední bajt zkopírovat úvodní bajt? Následující potíže nevyřeší, protože může potenciálně přetéct vyrovnávací paměti:  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` Volání pokusí udělat správnou věc – úplné znak zkopírovat, jestli je 1 nebo 2 bajty. Ale v úvahu poslední znak zkopírovat nevešel vyrovnávací paměť Pokud znak je 2 bajtů široké nevyžaduje. Správným řešením je:  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 Tento kód testů pro přetečení vyrovnávací paměti je možný ve smyčce testování, pomocí `_mbclen` testování velikosti aktuální znak, na kterou odkazuje `sz`. Tím, že zavoláte na `_mbsnbcpy` funkce, můžete nahradit kód `while` smyčky pomocí jeden řádek kódu. Příklad:  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## <a name="see-also"></a>Viz také  
 [MBCS – tipy pro programování](../text/mbcs-programming-tips.md)