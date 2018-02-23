---
title: vscanf_s vwscanf_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- vscanf_s
- vwscanf_s
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
apitype: DLLExport
f1_keywords:
- _vtscanf_s
- vscanf_s
- vwscanf_s
dev_langs:
- C++
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cc430ec34cd294de0cbabc8553ddda4fedce9e2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="vscanfs-vwscanfs"></a>vscanf_s, vwscanf_s
Čtení formátovaných dat z standardní vstupní proud. Tyto verze nástroje [vscanf vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int vscanf_s(  
   const char *format,  
   va_list arglist  
);   
int vwscanf_s(  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `format`  
 Řetězec formátu ovládacího prvku.  
  
 `arglist`  
 Seznam argumentů s proměnnou.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí počet polí úspěšně převést a přiřazení; Návratová hodnota nezahrnuje pole, které byly pro čtení, ale není přiřazen. Vrácená hodnota 0 značí, že byly přiřazené žádné pole. Vrácená hodnota je `EOF` pro chybu, nebo pokud je zjištěn znak end souborového nebo znak ukončení řetězce v první pokus o čtení znak. Pokud `format` je `NULL` ukazatele, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `vscanf_s` a `vwscanf_s` vrátit `EOF` a nastavte `errno` k `EINVAL`.  
  
 Informace o těchto a dalších kódy chyb naleznete v tématu [errno, _doserrno –, _sys_errlist – a _sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Poznámky  
 `vscanf_s` Funkce čte data z standardní vstupní proud `stdin` a zapisuje data do umístění, která se poskytují `arglist` seznam argumentů. Každý argument v seznamu musí být ukazatel na proměnné typu, která odpovídá specifikátor typu v `format`. Pokud ke kopírování dojde mezi řetězci, které se překrývají, chování není definováno.  
  
 `vwscanf_s` široká charakterová verze `vscanf_s`; `format` argument `vwscanf_s` je široká charakterová řetězec. `vwscanf_s` a `vscanf_s` chovají stejně jako datový proud se při otevření v režimu ANSI. `vscanf_s` vstup z datového proudu kódování UNICODE nepodporuje.  
  
 Na rozdíl od `vscanf` a `vwscanf`, `vscanf_s` a `vwscanf_s` vyžadují na velikost vyrovnávací paměti je možné zadat pro všechny vstupní parametry typu `c`, `C`, `s`, `S`, nebo string řízení sad, které jsou v `[]`. Velikost vyrovnávací paměti ve znacích je předán jako dodatečný parametr okamžitě následující ukazatele do vyrovnávací paměti nebo proměnnou. Velikost vyrovnávací paměti ve znacích `wchar_t` řetězec není stejná jako velikost v bajtech.  
  
 Velikost vyrovnávací paměti zahrnuje ukončující hodnotu null. Specifikace šířky pole můžete použít k zajištění, že token, který je pro čtení v se vejde do vyrovnávací paměti. Pokud se používá žádné pole Specifikace šířky a token, přečtěte si je příliš velký, aby se vešla do vyrovnávací paměti, nic se zapíše do této vyrovnávací paměti.  
  
> [!NOTE]
>  Parametr velikosti je typu `unsigned`, nikoli `size_t`.  
  
 Další informace najdete v tématu [specifikace šířky scanf](../../c-runtime-library/scanf-width-specification.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtscanf_s`|`vscanf_s`|`vscanf_s`|`vwscanf_s`|  
  
 Další informace najdete v tématu [pole Specifikace formátu: funkce scanf a wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`vscanf_s`|\<stdio.h>|  
|`wscanf_s`|\<stdio.h > nebo \<wchar.h >|  
  
Konzole není podporována v aplikacích pro univerzální platformu Windows (UWP). Standardní datový proud obslužných rutin, které jsou spojeny s konzolou, `stdin`, `stdout`, a `stderr`, C běhové funkce mohli používat v aplikacích pro UPW, musí být přesměrována. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).
  
## <a name="example"></a>Příklad  
  
```  
// crt_vscanf_s.c  
// compile with: /W3  
// This program uses the vscanf_s and vwscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vscanf_s(char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int call_vwscanf_s(wchar_t *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vwscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    int   i, result;  
    float fp;  
    char  c, s[81];  
    wchar_t wc, ws[81];  
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,  
                           &wc, 1, s, _countof(s), ws, _countof(ws) );  
    printf( "The number of fields input is %d\n", result );  
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                            &wc, 1, s, _countof(s), ws, _countof(ws) );  
    wprintf( L"The number of fields input is %d\n", result );  
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
  
```  
  
 Pokud tento program je uveden v příkladu vstupu, vyvolá tento výstup:  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
```Output  
The number of fields input is 6  
The contents are: 71 98.599998 h z Byte characters  
The number of fields input is 6  
The contents are: 36 92.300003 y n Wide characters  
```  
  
## <a name="see-also"></a>Viz také  
 [Podpora plovoucí desetinné čárky](../../c-runtime-library/floating-point-support.md)   
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [vscanf, vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md)