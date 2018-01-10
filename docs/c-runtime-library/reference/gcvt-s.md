---
title: "_gcvt_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _gcvt_s
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
- _gcvt_s
- gcvt_s
dev_langs: C++
helpviewer_keywords:
- _gcvt_s function
- _CVTBUFSIZE
- floating-point functions, converting number to string
- gcvt_s function
- numbers, converting to strings
- conversions, floating point to strings
- strings [C++], converting from floating point
- CVTBUFSIZE
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: "30"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a028431bb324fe634ee30ae81eec6c2d3371441
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="gcvts"></a>_gcvt_s
Převede hodnotu s plovoucí desetinnou čárkou na řetězec. Toto je verze [_gcvt –](../../c-runtime-library/reference/gcvt.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Vyrovnávací paměť pro uložení výsledek převodu.  
  
 [v]`sizeInBytes`  
 Velikost vyrovnávací paměti.  
  
 [v]`value`  
 Hodnota má být převeden.  
  
 [v]`digits`  
 Počet platných číslic, které jsou uložené.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu. Pokud dojde k chybě z důvodu neplatný parametr (v následující tabulce najdete neplatné hodnoty), obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, je vrácena kód chyby. Kódy chyb jsou definovány v Errno.h. Seznam těchto chybách naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|Vrátí|Hodnota v`buffer`|  
|--------------|-------------------|-------------|--------------|------------|-----------------------|  
|`NULL`|všechny|všechny|všechny|`EINVAL`|Nedojde ke změně.|  
|Není `NULL` (odkazuje na platný paměti)|nula|všechny|všechny|`EINVAL`|Nedojde ke změně.|  
|Není `NULL` (odkazuje na platný paměti)|všechny|všechny|>= `sizeInBytes`|`EINVAL`|Nedojde ke změně.|  
  
 **Problémy se zabezpečením**  
  
 `_gcvt_s`může vygenerovat porušení přístupu, pokud `buffer` neodkazuje na platný paměti a není `NULL`.  
  
## <a name="remarks"></a>Poznámky  
 `_gcvt_s` Funkce převede s plovoucí desetinnou čárkou `value` na řetězec znaků (která zahrnuje desetinné čárky a možné přihlašovací bajtů) a ukládá řetězec v `buffer`. `buffer`musí být dostatečně velký na to, aby dokázala pojmout převedená hodnota plus ukončující prázdný znak, který se automaticky připojí. Vyrovnávací paměť délky `_CVTBUFSIZE` je dostatečná pro všechny plovoucí bodu hodnotu. Pokud velikost vyrovnávací paměti `digits` + 1 se používá, funkce nepřepíše do konce vyrovnávací paměti, takže je nutné zadat dostatečná vyrovnávací paměti pro tuto operaci. `_gcvt_s`pokusí se vytvořit `digits` číslic ve formátu desetinného čísla. Pokud ne, vyvolá `digits` číslic v exponenciálním formátu. Koncové nuly lze potlačit v převodu.  
  
 V jazyce C++ pomocí této funkce se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze této funkce nejprve doplní vyrovnávací paměti s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_gcvt_s`|\<stdlib.h >|\<Error.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
```Output  
Converted value: 1.2  
```  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [atof –, _atof_l –, _wtof –, _wtof_l –](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [_ecvt_s –](../../c-runtime-library/reference/ecvt-s.md)   
 [_fcvt_s –](../../c-runtime-library/reference/fcvt-s.md)   
 [_gcvt](../../c-runtime-library/reference/gcvt.md)