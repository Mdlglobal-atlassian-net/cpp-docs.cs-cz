---
title: _dupenv_s, _wdupenv_s
ms.date: 11/04/2016
api_name:
- _dupenv_s
- _wdupenv_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f66828e0941c2324d75797cbb1fa77bdfa184205
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942027"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Získá hodnotu z aktuálního prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
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

### <a name="parameters"></a>Parametry

*vyrovnávací paměti*<br/>
Vyrovnávací paměť pro uložení hodnoty proměnné

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí

## <a name="return-value"></a>Návratová hodnota

Nula při úspěchu – chybový kód při selhání.

Tyto funkce ověřují své parametry; Pokud je *vyrovnávací paměť* nebo *název_proměnné* **null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

Pokud tyto funkce nemůžou přidělit dostatek paměti, nastaví *vyrovnávací paměť* na **hodnotu null** a *NumberOfElements* na 0 a vrátí **ENOMEM**.

## <a name="remarks"></a>Poznámky

Funkce **_dupenv_s** vyhledá v seznamu proměnných prostředí pro *název_proměnné*. Pokud je proměnná nalezena, **_dupenv_s** přidělí vyrovnávací paměť a zkopíruje hodnotu proměnné do vyrovnávací paměti. Adresa vyrovnávací paměti a délka se vrátí do *vyrovnávací paměti* a *numberOfElements*. Díky přidělení samotné vyrovnávací paměti poskytuje **_dupenv_s** pohodlnější alternativu k [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Je zodpovědností volajícího programu uvolnit paměť voláním [Free](free.md).

Pokud se proměnná nenajde, pak je *vyrovnávací paměť* nastavená na **hodnotu null**, *numberOfElements* je nastavená na 0 a návratová hodnota je 0, protože tato situace není považována za chybovou podmínku.

Pokud si nejste zajímat velikost vyrovnávací paměti, můžete pro *numberOfElements*předat **hodnotu null** .

**_dupenv_s** nerozlišuje velká a malá písmena v operačním systému Windows. **_dupenv_s** používá kopii prostředí, na kterou odkazovala globální proměnná **_environ** pro přístup k prostředí. Diskuzi o **_environ**najdete v poznámkách v [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) .

Hodnota ve *vyrovnávací paměti* je kopií hodnoty proměnné prostředí. Úprava nemá žádný vliv na prostředí. Pro úpravu hodnoty proměnné prostředí použijte funkci [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md) .

**_wdupenv_s** je **_dupenv_s**verze s velkým znakem; argumenty **_wdupenv_s** jsou řetězce s velkým počtem znaků. Globální proměnná **_wenviron** je verze **_environ**s velkým znakem. Další informace o **_wenviron**najdete v poznámkách v [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) .

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
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

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
