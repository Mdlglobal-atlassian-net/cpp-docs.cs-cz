---
title: "strerror_s –, _strerror_s –, _wcserror_s –, __wcserror_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- __wcserror_s
- _strerror_s
- _wcserror_s
- strerror_s
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcserror_s
- __wcserror_s
- _tcserror_s
- _wcserror_s
- tcserror_s
- strerror_s
- _strerror_s
dev_langs:
- C++
helpviewer_keywords:
- __wcserror_s function
- error messages, printing
- tcserror_s function
- printing error messages
- strerror_s function
- _wcserror_s function
- _tcserror_s function
- _strerror_s function
- wcserror_s function
- error messages, getting
ms.assetid: 9e5b15a0-efe1-4586-b7e3-e1d7c31a03d6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 791f9b7408fded070fe61206d4303c26c8926d3e
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="strerrors-strerrors-wcserrors-wcserrors"></a>strerror_s, _strerror_s, _wcserror_s, __wcserror_s
Se objeví chybová zpráva systému (`strerror_s`, `_wcserror_s`) nebo vytisknout uživatelem zadané chybová zpráva (`_strerror_s`, `__wcserror_s`). Toto jsou verze [strerror – _strerror –, _wcserror –, \__wcserror –](../../c-runtime-library/reference/strerror-strerror-wcserror-wcserror.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t _strerror_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *strErrMsg   
);  
errno_t _wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   int errnum   
);  
errno_t __wcserror_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *strErrMsg   
);  
template <size_t size>  
errno_t strerror_s(  
   char (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t _strerror_s(  
   char (&buffer)[size],  
   const char *strErrMsg   
); // C++ only  
template <size_t size>  
errno_t _wcserror_s(  
   wchar_t (&buffer)[size],  
   int errnum   
); // C++ only  
template <size_t size>  
errno_t __wcserror_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *strErrMsg   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Vyrovnávací paměti pro uložení řetězec chyby.  
  
 `numberOfElements`  
 Velikost vyrovnávací paměti.  
  
 `errnum`  
 Číslo chyby.  
  
 `strErrMsg`  
 Uživatelem zadané zprávy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání.  
  
### <a name="error-condtions"></a>Chyba způsobilost  
  
|`buffer`|`numberOfElements`|`strErrMsg`|Obsah `buffer`|  
|--------------|------------------------|-----------------|--------------------------|  
|`NULL`|všechny|všechny|není k dispozici|  
|všechny|0|všechny|nedojde ke změně|  
  
## <a name="remarks"></a>Poznámky  
 `strerror_s` Funkce mapy `errnum` na řetězec chybová zpráva, vrátí řetězec v `buffer`. `_strerror_s` neberou číslo chyby; používá aktuální hodnota `errno` určit příslušnou zprávu. Ani `strerror_s` ani `_strerror_s` ve skutečnosti vytiskne zprávy:, takže je třeba volat výstup funkce, jako [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
{  
   _strerror_s(buffer, 80);  
   fprintf( stderr, buffer );  
}  
```  
  
 Pokud `strErrMsg` je `NULL`, `_strerror_s` vrátí řetězec v `buffer` obsahující chybovou zprávu systému pro posledního volání knihovny, které je chyba. Řetězec chybová zpráva se ukončila příkazem znak nového řádku (\n). Pokud `strErrMsg` se nerovná `NULL`, pak `_strerror_s` vrátí řetězec v `buffer` obsahující (v pořadí) řetězce zprávy, středník, mezeru, chybová zpráva systému poslední volání knihovny generovala k chybě a znak nového řádku. Řetězce zprávy může být maximálně 94 znaků.  
  
 Tyto funkce zkrátit chybovou zprávu, pokud jeho délka přesahuje `numberOfElements` -1. Výsledný řetězec v `buffer` je vždy ukončené hodnotou null.  
  
 Číslo chyby pro `_strerror_s` je uložené v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Systém chybové zprávy, které jsou přístupné prostřednictvím proměnnou [_sys_errlist –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md), což je pole zpráv, které jsou seřazené podle číslo chyby. `_strerror_s` přistupuje k příslušná chybová zpráva s použitím `errno` hodnotu jako index pro proměnnou `_sys_errlist`. Hodnota proměnné [_sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) je definován jako maximální počet elementů v `_sys_errlist` pole. Chcete-li vytvořit přesné výsledky, volejte `_strerror_s` ihned po rutiny knihovny vrátí chybu. Jinak, následných volání `strerror_s` nebo `_strerror_s` můžete přepsat `errno` hodnotu.  
  
 `_wcserror_s` a `__wcserror_s` jsou verze široká charakterová `strerror_s` a `_strerror_s`, v uvedeném pořadí.  
  
 Tyto funkce ověřit jejich parametrů. Pokud vyrovnávací paměť je `NULL` nebo pokud je parametr velikosti 0, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md) . Pokud je povoleno spuštění chcete-li pokračovat, vrátí funkce `EINVAL` a nastavte `errno` k `EINVAL`.  
  
 `_strerror_s`, `_wcserror_s`, a `__wcserror_s` nejsou součástí definice ANSI ale místo toho jsou rozšíření Microsoft pro ho. Nepoužívejte je kde je žádoucí přenositelnost; ANSI kompatibility, použijte `strerror_s` místo.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
 Ladicí verze těchto funkcí nejprve vyplnit vyrovnávací paměť s 0xFD. Chcete-li toto chování zakázat, použijte [_crtsetdebugfillthreshold –](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror_s`|`strerror_s`|`strerror_s`|`_wcserror_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strerror_s`, `_strerror_s`|\<String.h >|  
|`_wcserror_s`, `__wcserror_s`|\<String.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [perror](../../c-runtime-library/reference/perror-wperror.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr](../../c-runtime-library/reference/clearerr.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror](../../c-runtime-library/reference/perror-wperror.md)