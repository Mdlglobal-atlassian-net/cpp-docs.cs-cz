---
title: _dupenv_s, _wdupenv_s
ms.date: 11/04/2016
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
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: bc8af3282b57c9fa411aac97f5fa4d414bc3305b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62288859"
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s

Získá hodnotu z aktuálního prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Vyrovnávací paměti*<br/>
Vyrovnávací paměť pro ukládání hodnotu proměnné.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*varname*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; při selhání kód chyby.

Tyto funkce ověřují své parametry; Pokud *vyrovnávací paměti* nebo *název_proměnné* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, funkce nastaví **errno** k **EINVAL** a vrátit **EINVAL**.

Pokud těmto funkcím nelze přidělit dostatek paměti, že nastavené *vyrovnávací paměti* k **NULL** a *numberOfElements* na 0 a vrátí **ENOMEM**.

## <a name="remarks"></a>Poznámky

**_Dupenv_s –** funkce prohledává seznam proměnných prostředí pro *název_proměnné*. Pokud proměnná není nalezena, **_dupenv_s –** přidělí vyrovnávací paměť a kopíruje do vyrovnávací paměti hodnotu proměnné. Adresu a délku vyrovnávací paměti jsou vráceny v *vyrovnávací paměti* a *numberOfElements*. Přidělením samotné vyrovnávací paměti **_dupenv_s –** poskytuje pohodlnější alternativu k [getenv_s – _wgetenv_s –](getenv-s-wgetenv-s.md).

> [!NOTE]
> Je odpovědností volajícího programu uvolnit paměť pomocí volání [bezplatné](free.md).

Pokud není nalezena proměnné, pak *vyrovnávací paměti* je nastavena na **NULL**, *numberOfElements* je nastavena na hodnotu 0, a návratová hodnota je 0, protože tato situace není považována za chybu Podmínka.

Pokud si nejste zájem o velikost vyrovnávací paměti lze předat **NULL** pro *numberOfElements*.

**_dupenv_s –** není malá a velká písmena v operačním systému Windows. **_dupenv_s –** použije kopii prostředí, na které odkazuje globální proměnnou **_environ** pro přístup k prostředí. Viz poznámky v [getenv_s – _wgetenv_s –](getenv-s-wgetenv-s.md) diskuzi o **_environ**.

Hodnota v *vyrovnávací paměti* je kopie hodnoty proměnné prostředí; její změna nemá žádný vliv na prostředí. Použití [_putenv_s _wputenv_s –](putenv-s-wputenv-s.md) funkce ke změně hodnoty proměnné prostředí.

**_wdupenv_s –** je verze širokého znaku **_dupenv_s –**; argumenty **_wdupenv_s –** jsou širokoznaké řetězce. **_Wenviron** globální proměnná je verze širokého znaku **_environ**. Viz poznámky v [getenv_s – _wgetenv_s –](getenv-s-wgetenv-s.md) pro další informace o **_wenviron**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
