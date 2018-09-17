---
title: _set_output_format – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _set_output_format
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- set_output_format
- _set_output_format
dev_langs:
- C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de9ce3ad9d5f1a39fb1ed173dc430aa9a5c5127c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701490"
---
# <a name="setoutputformat"></a>_set_output_format
Přizpůsobí výstupních formátů používaných sadou formátovaný vstupních/výstupních funkcí.  
  
> [!IMPORTANT]
>  Tato funkce je zastaralá. Od v sadě Visual Studio 2015, není k dispozici v CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### <a name="parameters"></a>Parametry  
*Formát*<br/>
[in] Hodnotu představující formátu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výstupní formát.  
  
## <a name="remarks"></a>Poznámky  
 `_set_output_format` slouží ke konfiguraci výstupu formátovaných vstupních/výstupních funkcí, jako [printf_s](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). V současné době je pouze konvence formátování, změněné touto funkcí počet číslic zobrazených v exponenty ve výstupu příkazu plovoucí desetinnou čárkou.  
  
 Ve výchozím nastavení, výstup s plovoucí desetinnou čárkou bodu čísla pomocí funkcí, jako `printf_s`, `wprintf_s`, a související funkce v knihovně nástroje Visual C++ Standard C vytiskne tří číslic exponentu, i v případě, že není nutné tři číslice představující hodnotu exponent. Nuly se používají k vyplnění hodnota, která má tři číslice. `_set_output_format` umožňuje toto chování změnit tak, aby vypsaných pouze dvě číslice v exponentu Pokud třetí číslici vyžaduje velikost exponent.  
  
 Pokud chcete povolit exponenty dvěma číslicemi, voláním této funkce s parametrem `_TWO_DIGIT_EXPONENT`, jak je znázorněno v příkladu. Chcete-li zakázat exponenty dvě číslice, voláním této funkce s parametrem 0.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_output_format`|\<stdio.h>|  
  
 Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```C  
// crt_set_output_format.c  
#include <stdio.h>  
  
void printvalues(double x, double y)  
{  
   printf_s("%11.4e %11.4e\n", x, y);  
   printf_s("%11.4E %11.4E\n", x, y);  
   printf_s("%11.4g %11.4g\n", x, y);  
   printf_s("%11.4G %11.4G\n", x, y);  
}  
  
int main()  
{  
   double x = 1.211E-5;  
   double y = 2.3056E-112;  
   unsigned int old_exponent_format;  
  
   // Use the default format  
   printvalues(x, y);  
  
   // Enable two-digit exponent format  
   old_exponent_format = _set_output_format(_TWO_DIGIT_EXPONENT);  
  
   printvalues(x, y);  
  
   // Disable two-digit exponent format  
   _set_output_format( old_exponent_format );  
  
   printvalues(x, y);  
}  
```  
  
```Output  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
 1.2110e-05 2.3056e-112  
 1.2110E-05 2.3056E-112  
  1.211e-05  2.306e-112  
  1.211E-05  2.306E-112  
1.2110e-005 2.3056e-112  
1.2110E-005 2.3056E-112  
 1.211e-005  2.306e-112  
 1.211E-005  2.306E-112  
```  
  
## <a name="see-also"></a>Viz také  
 [printf_s, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_get_output_format](../c-runtime-library/get-output-format.md)