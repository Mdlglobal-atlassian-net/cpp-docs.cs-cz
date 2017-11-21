---
title: "_atodbl –, _atodbl_l –, _atoldbl –, _atoldbl_l –, _atoflt –, _atoflt_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _atoldbl
- _atoldbl_l
- _atodbl
- _atoflt
- _atoflt_l
- _atodbl_l
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _atoflt
- _atoflt_l
- atodbl_l
- atoflt_l
- _atoldbl
- _atoldbl_l
- atodbl
- _atodbl_l
- atoldbl
- atoflt
- atoldbl_l
- _atodbl
dev_langs: C++
helpviewer_keywords:
- _atodbl function
- _atoldbl_l function
- atoflt function
- atoflt_l function
- atoldbl function
- _atoldbl function
- atodbl_l function
- _atoflt_l function
- atoldbl_l function
- atodbl function
- string conversion, to floating point values
- _atoflt function
- _atodbl_l function
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5c845d5662e8193f1a4e3c3357086bd207696559
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atodbl-atodbll-atoldbl-atoldbll-atoflt-atofltl"></a>_atodbl –, _atodbl_l –, _atoldbl –, _atoldbl_l –, _atoflt –, _atoflt_l –
Převede řetězec na dvojitou hodnotu (`_atodbl`), long double (`_atoldbl`), nebo float (`_atoflt`).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _atodbl(  
   _CRT_DOUBLE * value,  
   char * str  
);  
int _atodbl_l (  
   _CRT_DOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoldbl(  
   _LDOUBLE * value,  
   char * str  
);  
int _atoldbl_l (  
   _LDOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoflt(  
   _CRT_FLOAT * value,  
   const char * str  
);  
int _atoflt_l(  
   _CRT_FLOAT * value,  
   const char * str,  
   locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Double, dlouhé double, nebo float hodnotu, která je produkovaný převádění řetězec na hodnotu s plovoucí desetinnou čárkou. Tyto hodnoty jsou zabalená ve struktuře.  
  
 `str`  
 Řetězec, který má být analyzován převést na hodnotu s plovoucí desetinnou čárkou.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí hodnotu 0. Možné chybové kódy jsou `_UNDERFLOW` nebo `_OVERFLOW`, které jsou definovány v záhlaví souboru Math.h.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce převést řetězec na hodnotu s plovoucí desetinnou čárkou. Rozdíl mezi tyto funkce a `atof` řady funkcí je, že tyto funkce nejsou generování kódu s plovoucí desetinnou čárkou a nezpůsobí výjimky hardwaru. Namísto toho chybové stavy jsou považovány za kódy chyb.  
  
 Pokud řetězec není platný interpretaci jako hodnotu s plovoucí desetinnou čárkou `value` je nastavena na nulu a návratový je hodnota nulová.  
  
 Verze tyto funkce, které mají `_l` příponu jsou stejné verze, které nemají příponu, s výjimkou toho, aby využívaly parametr národního prostředí, který se předává v místo aktuální národní prostředí vlákna.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutiny|Požadovaný hlavičkový soubor|  
|--------------|---------------------|  
|`_atodbl`, `_atoldbl`, `_atoflt`<br /><br /> `_atodbl_l`, `_atoldbl_l`, `_atoflt_l`|\<stdlib.h >|  
  
## <a name="example"></a>Příklad  
  
```  
// crt_atodbl.c  
// Uses _atodbl to convert a string to a double precision  
// floating point value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
   char str1[256] = "3.141592654";  
   char abc[256] = "abc";  
   char oflow[256] = "1.0E+5000";  
   _CRT_DOUBLE dblval;  
   _CRT_FLOAT fltval;  
   int retval;  
  
   retval = _atodbl(&dblval, str1);  
  
   printf("Double value: %lf\n", dblval.x);  
   printf("Return value: %d\n\n", retval);  
  
   retval = _atoflt(&fltval, str1);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // A non-floating point value: returns 0.  
   retval = _atoflt(&fltval, abc);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // Overflow.  
   retval = _atoflt(&fltval, oflow);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   return 0;  
}  
```  
  
```Output  
Double value: 3.141593  
Return value: 0  
  
Float value: 3.141593  
Return value: 0  
  
Float value: 0.000000  
Return value: 0  
  
Float value: 1.#INF00  
Return value: 3  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)