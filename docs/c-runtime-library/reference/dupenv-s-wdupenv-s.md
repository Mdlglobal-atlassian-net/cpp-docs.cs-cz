---
title: _dupenv_s, _wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348063"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Získá hodnotu z aktuálního prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Vyrovnávací paměť pro uložení hodnoty proměnné.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název var*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula na úspěch, kód chyby na selhání.

Tyto funkce ověřují jejich parametry; Pokud je *vyrovnávací paměť* nebo *název varnull* , je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části Ověření [parametru](../../c-runtime-library/parameter-validation.md). **NULL** Pokud je spuštění povoleno pokračovat, funkce nastavit **errno** na **EINVAL** a vrátit **EINVAL**.

Pokud tyto funkce nelze přidělit dostatek paměti, nastaví *vyrovnávací paměť* na **HODNOTU NULL** a *numberOfElements* na 0 a vrátí **ENOMEM**.

## <a name="remarks"></a>Poznámky

Funkce **_dupenv_s** prohledá seznam proměnných prostředí pro *název varname*. Pokud je proměnná nalezena, **_dupenv_s** přiděluje vyrovnávací paměť a zkopíruje hodnotu proměnné do vyrovnávací paměti. Adresa a délka vyrovnávací paměti jsou *vráceny* ve vyrovnávací paměti a *numberOfElements*. Přidělením vyrovnávací paměti sám, **_dupenv_s** poskytuje pohodlnější alternativu k [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Je odpovědností volajícího programu uvolnit paměť voláním [free](free.md).

Pokud proměnná není nalezena, je *vyrovnávací paměť* nastavena na **hodnotu NULL**, *numberOfElements* je nastavena na hodnotu 0 a vrácená hodnota je 0, protože tato situace není považována za chybovou podmínku.

Pokud nemáte zájem o velikost vyrovnávací paměti můžete předat **NULL** pro *numberOfElements*.

**_dupenv_s** v operačním systému Windows nerozlišují malá a velká písmena. **_dupenv_s** používá kopii prostředí, na kterou se vztahuje globální proměnná **_environ** pro přístup k prostředí. Informace o **_environ**naleznete v _wgetenv_s poznámky v [getenv_s.](getenv-s-wgetenv-s.md)

Hodnota ve *vyrovnávací paměti* je kopií hodnoty proměnné prostředí; jeho úprava nemá žádný vliv na životní prostředí. Pomocí [funkce _putenv_s _wputenv_s](putenv-s-wputenv-s.md) upravte hodnotu proměnné prostředí.

**_wdupenv_s** je širokoznaková verze **_dupenv_s**; argumenty **_wdupenv_s** jsou řetězce širokých znaků. Globální proměnná **_wenviron** je verze **_environ**s širokými znaky . Další informace o _wenviron najdete v getenv_s poznámkách [v](getenv-s-wgetenv-s.md) **_wgetenv_s**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[Environmentální konstanty](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
