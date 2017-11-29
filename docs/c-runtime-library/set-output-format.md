---
title: "_set_output_format – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_output_format
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
dev_langs: C++
helpviewer_keywords:
- _TWO_DIGIT_EXPONENT constant
- output formatting
- TWO_DIGIT_EXPONENT constant
- _set_output_format function
- set_output_format function
ms.assetid: 1cb48df8-44b4-4400-bd27-287831d6b3ff
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 937a452b145fd3d30518f8c4b786ab79b46d5cea
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="setoutputformat"></a>_set_output_format
Přizpůsobí výstupní formáty používané funkce formátovaný vstupně-výstupní operace.  
  
> [!IMPORTANT]
>  Tato funkce je zastaralé. Od verze sady Visual Studio 2015, není k dispozici v CRT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _set_output_format(  
   unsigned int format  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`format`  
 Hodnotu představující formát, který se použije.  
  
## <a name="return-value"></a>Návratová hodnota  
 Výstupní formát.  
  
## <a name="remarks"></a>Poznámky  
 `_set_output_format`slouží ke konfiguraci výstup naformátovaný funkce vstupně-výstupních operací, jako [printf_s –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md). V současné době pouze formátování konvence, která lze změnit pomocí této funkce je počet číslic, na které se zobrazí v exponenty ve výstupu plovoucí desetinnou čárkou.  
  
 Ve výchozím nastavení, výstup plovoucí bodu čísla pomocí funkce, jako `printf_s`, `wprintf_s`, a související funkce v knihovně Visual C++ standardní C vytiskne tří číslic pro exponent, i v případě tří číslic nemusejí představují hodnota exponent. Nul se používají k vyplnění hodnota, která má tři znaky. `_set_output_format`umožňuje toto chování změnit tak, aby pouze dvě číslice jsou vytištěn v exponent, pokud je velikost exponent nevyžaduje třetí číslice.  
  
 Povolit letopočty exponenty, volání této funkce s parametrem `_TWO_DIGIT_EXPONENT`, jak je znázorněno v příkladu. Zakázat dvě číslice exponenty, volejte tuto funkci s argumentem 0.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_set_output_format`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md) v úvodu.  
  
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
 [printf_s –, _printf_s_l –, wprintf_s –, _wprintf_s_l –](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [_get_output_format –](../c-runtime-library/get-output-format.md)