---
title: "strerror –, _strerror –, _wcserror –, __wcserror – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- strerror
- _strerror
- _wcserror
- __wcserror
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
- __sys_errlist
- wcserror
- _strerror
- __wcserror
- strerror
- __sys_nerr
- _tcserror
- _wcserror
- tcserror
dev_langs: C++
helpviewer_keywords:
- strerror function
- _strerror function
- __sys_errlist
- wcserror function
- error messages, printing
- __sys_nerr
- tcserror function
- printing error messages
- _wcserror function
- _tcserror function
- __wcserror function
- error messages, getting
ms.assetid: 27b72255-f627-43c0-8836-bcda8b003e14
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b534c0a43c78c42265fa3b36aca523dc27e170fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="strerror-strerror-wcserror-wcserror"></a>strerror, _strerror, _wcserror, __wcserror
Získá řetězec chybové zprávy systému (`strerror`, `_wcserror`) nebo formáty řetězec uživatelem zadané chybové zprávy (`_strerror`, `__wcserror`). Bezpečnější verze tyto funkce jsou k dispozici. v tématu [strerror_s – _strerror_s –, _wcserror_s –, \__wcserror_s –](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *strerror(  
   int errnum   
);  
char *_strerror(  
   const char *strErrMsg   
);  
wchar_t * _wcserror(  
   int errnum   
);  
wchar_t * __wcserror(  
   const wchar_t *strErrMsg   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `errnum`  
 Číslo chyby.  
  
 `strErrMsg`  
 Uživatelem zadané zprávy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto funkce vrátí ukazatel na řetězec chybová zpráva. Následující volání můžete přepsat řetězec.  
  
## <a name="remarks"></a>Poznámky  
 `strerror` Funkce mapy `errnum` na řetězec chybová zpráva a vrací ukazatel na řetězec. Ani `strerror` ani `_strerror` ve skutečnosti vytiskne zprávy:, takže máte například zavolat funkci výstup [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md):  
  
```  
if (( _access( "datafile",2 )) == -1 )  
   fprintf( stderr, _strerror(NULL) );  
```  
  
 Pokud `strErrMsg` se předá jako `NULL`, `_strerror` vrací ukazatel na řetězec, který obsahuje chybovou zprávu systému pro posledního volání knihovny, které je chyba. Řetězec chybová zpráva se ukončila příkazem znak nového řádku (\n). Pokud `strErrMsg` se nerovná `NULL`, pak `_strerror` vrací ukazatel na řetězec, který obsahuje (v pořadí) řetězce zprávy, středník, mezeru, chybová zpráva systému pro posledního volání knihovny, které vytváří k chybě a znak nového řádku. Řetězce zprávy může být maximálně 94 znaků.  
  
 Číslo chyby pro `_strerror` je uložené v proměnné [errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Chcete-li vytvořit přesné výsledky, volejte `_strerror` ihned po rutiny knihovny vrátí chybu. Jinak, následných volání `strerror` nebo `_strerror` můžete přepsat `errno` hodnotu.  
  
 `_wcserror`a `__wcserror` jsou verze široká charakterová `strerror` a `_strerror`, v uvedeném pořadí.  
  
 `_strerror`, `_wcserror`, a `__wcserror` nejsou součástí definice ANSI; jsou rozšíření Microsoft a doporučujeme vám, že nepoužíváte je místo, kam chcete přenosné kódu. ANSI kompatibility, použijte `strerror` místo.  
  
 Pokud chcete získat chyba řetězce, doporučujeme, abyste `strerror` nebo `_wcserror` místo nepoužívané makra [_sys_errlist –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a [_sys_nerr –](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) a nepoužívané interní funkce `__sys_errlist` a `__sys_nerr`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcserror`|`strerror`|`strerror`|`_wcserror`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`strerror`|\<String.h >|  
|`_strerror`|\<String.h >|  
|`_wcserror`, `__wcserror`|\<String.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [perror](../../c-runtime-library/reference/perror-wperror.md).  
  
## <a name="see-also"></a>Viz také  
 [Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)   
 [clearerr –](../../c-runtime-library/reference/clearerr.md)   
 [ferror –](../../c-runtime-library/reference/ferror.md)   
 [perror, _wperror –](../../c-runtime-library/reference/perror-wperror.md)