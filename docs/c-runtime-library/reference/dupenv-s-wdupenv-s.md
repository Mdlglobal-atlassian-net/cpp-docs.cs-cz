---
title: "_dupenv_s –, _wdupenv_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
dev_langs: C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c42da9004dc5ea63179d94a36335db3932f5d23b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s
Získá hodnotu z aktuální prostředí.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _dupenv_s(  
   char **buffer,  
   size_t *numberOfElements,  
   const char *varname  
);  
errno_t _wdupenv_s(  
   wchar_t **buffer,  
   size_t *numberOfElements,  
   const wchar_t *varname  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Vyrovnávací paměť pro uložení hodnota proměnné.  
  
 `numberOfElements`  
 Velikost `buffer`.  
  
 `varname`  
 Název proměnné prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Nula v případě úspěchu, kód chyby při selhání.  
  
 Tyto funkce ověřit jejich parametrů; Pokud `buffer` nebo `varname` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, nastavte funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
 Pokud tyto funkce nemůže přidělit dostatek paměti, nastavují `buffer` k `NULL` a `numberOfElements` 0, a vrátí `ENOMEM`.  
  
## <a name="remarks"></a>Poznámky  
 `_dupenv_s` Funkce vyhledá seznamu proměnných prostředí pro `varname`. Pokud je nalezena proměnná, `_dupenv_s` přiděluje vyrovnávací paměť a zkopíruje hodnota proměnné do vyrovnávací paměti. Adresa a délka vyrovnávací paměti na jsou vráceny v `buffer` a `numberOfElements`. Přidělí vyrovnávací paměť samostatně, `_dupenv_s` poskytuje pohodlnější alternativa k [getenv_s –, _wgetenv_s –](../../c-runtime-library/reference/getenv-s-wgetenv-s.md).  
  
> [!NOTE]
>  Odpovídá volací program uvolnit paměť voláním [volné](../../c-runtime-library/reference/free.md).  
  
 Pokud není nalezena proměnná, pak `buffer` je nastaven na `NULL`, `numberOfElements` je nastaven na hodnotu 0, a návratová hodnota je 0, protože tato situace se nepovažuje za chybový stav.  
  
 Pokud si nejste zájem o velikost vyrovnávací paměti můžete předat `NULL` pro `numberOfElements`.  
  
 `_dupenv_s`není malá a velká písmena v operačním systému Windows. `_dupenv_s`používá kopii ukazující na globální proměnnou prostředí `_environ` pro přístup k prostředí. V části poznámky v [getenv_s –, _wgetenv_s –](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) diskuzi o `_environ`.  
  
 Hodnota v `buffer` je kopie hodnota proměnné prostředí; jeho změnou nemá žádný vliv na prostředí. Použití [_putenv_s –, _wputenv_s –](../../c-runtime-library/reference/putenv-s-wputenv-s.md) funkce ke změně hodnoty proměnné prostředí.  
  
 `_wdupenv_s`široká charakterová verze `_dupenv_s`; argumenty `_wdupenv_s` jsou široká charakterová řetězce. `_wenviron` – Globální proměnná je verze široká charakterová `_environ`. V části poznámky v [getenv_s –, _wgetenv_s –](../../c-runtime-library/reference/getenv-s-wgetenv-s.md) Další informace o `_wenviron`.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tdupenv_s`|`_dupenv_s`|`_dupenv_s`|`_wdupenv_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_dupenv_s`|\<stdlib.h >|  
|`_wdupenv_s`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_dupenv_s.c  
#include  <stdlib.h>  
  
int main( void )  
{  
   char *pValue;  
   size_t len;  
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );  
   if ( err ) return -1;  
   printf( "pathext = %s\n", pValue );  
   free( pValue );  
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );  
   if ( err ) return -1;  
   printf( "nonexistentvariable = %s\n", pValue );  
   free( pValue ); // It's OK to call free with NULL  
}  
```  
  
## <a name="sample-output"></a>Vzorový výstup  
  
```  
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl  
nonexistentvariable = (null)  
```  
  
## <a name="see-also"></a>Viz také  
 [Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)   
 [Konstanty prostředí](../../c-runtime-library/environmental-constants.md)   
 [_dupenv_s_dbg –, _wdupenv_s_dbg –](../../c-runtime-library/reference/dupenv-s-dbg-wdupenv-s-dbg.md)   
 [getenv_s –, _wgetenv_s –](../../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [_putenv_s –, _wputenv_s –](../../c-runtime-library/reference/putenv-s-wputenv-s.md)