---
title: "_get_output_format – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _get_output_format
apilocation:
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
apitype: DLLExport
f1_keywords:
- get_output_format
- _get_output_format
dev_langs: C++
helpviewer_keywords:
- output formatting
- get_output_format function
- _get_output_format function
ms.assetid: 0ce42f3b-3479-41c4-bcbf-1d21f7ee37e7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c07981e3faed2b7d1a55140081c0be254049825
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getoutputformat"></a>_get_output_format
Získá aktuální hodnotu příznak formát výstupu.  
  
> [!IMPORTANT]
>  Tato funkce je zastaralé. Od verze sady Visual Studio 2015, není k dispozici v CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _get_output_format();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Aktuální hodnota příznak formát výstupu.  
  
## <a name="remarks"></a>Poznámky  
 Příznak formát výstupu řídí funkce formátovaný vstupně-výstupních operací. V současné době příznak má dvě možné hodnoty: 0 a `_TWO_DIGIT_EXPONENT`. Pokud `_TWO_DIGIT_EXPONENT` je nastaven plovoucí bodu čísla je vytištěna s pouze dvěma číslic exponentu Pokud je velikost exponent nevyžaduje třetí číslice. Pokud příznak nula, plovoucí desetinné čárky výstup zobrazuje tři číslice exponent, pomocí nuly v případě potřeby k vyplnění hodnota, která má tři znaky.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_get_output_format`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
[Syntaxe specifikace formátu: funkce printf a wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)  
 [printf, _printf_l –, wprintf, _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_set_output_format –](../c-runtime-library/set-output-format.md)  
