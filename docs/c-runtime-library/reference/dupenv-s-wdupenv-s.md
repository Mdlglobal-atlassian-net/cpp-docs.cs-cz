---
title: _dupenv_s –, _wdupenv_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5a918b866b0b43fb0e6b31e2deb5d9861dabe9a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402111"
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s, _wdupenv_s

Získá hodnotu z aktuální prostředí.

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Vyrovnávací paměť pro uložení hodnota proměnné.

*numberOfElements*<br/>
Velikost *vyrovnávací paměti*.

*název_proměnné*<br/>
Název proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu, kód chyby při selhání.

Tyto funkce ověřit jejich parametrů; Pokud *vyrovnávací paměti* nebo *název_proměnné* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, nastavte funkce **errno** k **einval –** a vrátit **einval –**.

Pokud tyto funkce nemůže přidělit dostatek paměti, nastavují *vyrovnávací paměti* k **NULL** a *numberOfElements* 0, a vrátí **enomem –**.

## <a name="remarks"></a>Poznámky

**_Dupenv_s –** funkce vyhledá seznamu proměnných prostředí pro *název_proměnné*. Pokud je nalezena proměnná, **_dupenv_s –** přiděluje vyrovnávací paměť a zkopíruje hodnota proměnné do vyrovnávací paměti. Adresa a délka vyrovnávací paměti na jsou vráceny v *vyrovnávací paměti* a *numberOfElements*. Přidělí vyrovnávací paměť samostatně, **_dupenv_s –** poskytuje pohodlnější alternativa k [getenv_s –, _wgetenv_s –](getenv-s-wgetenv-s.md).

> [!NOTE]
> Odpovídá volací program uvolnit paměť voláním [volné](free.md).

Pokud není nalezena proměnná, pak *vyrovnávací paměti* je nastaven na **NULL**, *numberOfElements* je nastaven na hodnotu 0, a návratová hodnota je 0, protože tato situace se nepovažuje za chybu Podmínka.

Pokud si nejste zájem o velikost vyrovnávací paměti můžete předat **NULL** pro *numberOfElements*.

**_dupenv_s –** není malá a velká písmena v operačním systému Windows. **_dupenv_s –** používá kopii ukazující na globální proměnnou prostředí **_environ –** pro přístup k prostředí. V části poznámky v [getenv_s –, _wgetenv_s –](getenv-s-wgetenv-s.md) diskuzi o **_environ –**.

Hodnota v *vyrovnávací paměti* je kopie hodnota proměnné prostředí; jeho změnou nemá žádný vliv na prostředí. Použití [_putenv_s –, _wputenv_s –](putenv-s-wputenv-s.md) funkce ke změně hodnoty proměnné prostředí.

**_wdupenv_s –** je verze široká charakterová **_dupenv_s –**; argumenty **_wdupenv_s –** jsou široká charakterová řetězce. **_Wenviron –** – globální proměnná je verze široká charakterová **_environ –**. V části poznámky v [getenv_s –, _wgetenv_s –](getenv-s-wgetenv-s.md) Další informace o **_wenviron –**.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s –**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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
[Konstanty prostředí](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
