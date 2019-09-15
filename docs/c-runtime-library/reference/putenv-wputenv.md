---
title: _putenv, _wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
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
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949884"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Vytvoří, změní nebo odebere proměnné prostředí. K dispozici jsou bezpečnější verze těchto funkcí; viz [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>Parametry

*envstring*<br/>
Definice řetězce prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí 0, pokud bylo úspěšné, nebo-1 v případě chyby.

## <a name="remarks"></a>Poznámky

Funkce **_putenv** přidá nové proměnné prostředí nebo upraví hodnoty stávajících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spouští (například výchozí cesta pro hledání knihoven, které mají být propojeny s programem). **_wputenv** je **_putenv**verze s velkým znakem; Argument *envstring* pro **_wputenv** je řetězec s velkým znakem.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Argument *envstring* musí být ukazatel na řetězec ve tvaru *název_proměnné*=*value_string*, kde *název_proměnné* je název proměnné prostředí, kterou chcete přidat nebo upravit, a *value_string* je proměnná osa. Pokud je hodnota *název_proměnné* již součástí prostředí, je její hodnota nahrazena hodnotou *value_string*; v opačném případě se nová proměnná *název_proměnné* a její hodnota *value_string* přidají do prostředí. Můžete odebrat proměnnou z prostředí zadáním prázdného *value_stringu*nebo jinými slovy zadáním pouze *název_proměnné*=.

**_putenv** a **_wputenv** ovlivňují jenom prostředí, které je pro aktuální proces místní. nelze je použít pro úpravu prostředí na úrovni příkazu. To znamená, že tyto funkce pracují pouze s datovými strukturami dostupnými pro běhovou knihovnu a nikoli s segmentem prostředí vytvořeným pro proces operačním systémem. Po ukončení aktuálního procesu se prostředí vrátí na úroveň volajícího procesu (ve většině případů na úrovni operačního systému). Upravené prostředí však lze předat všem novým procesům vytvořeným pomocí **_spawn**, **_exec**nebo **systému**a tyto nové procesy získají všechny nové položky přidané **_putenv** a **_wputenv**.

Neměňte položku prostředí přímo: místo toho pro změnu použijte **_putenv** nebo **_wputenv** . Konkrétně přímé uvolnění prvků v globálním poli **_environ []** může vést k adresování neplatné paměti.

**getenv** a **_putenv** používají globální proměnnou **_environ** pro přístup k tabulce prostředí; **_wgetenv** a **_wputenv** používají **_wenviron**. **_putenv** a **_wputenv** mohou změnit hodnotu **_environ** a **_wenviron**, čímž se neověřuje argument **_envp** **Main** a argument **_wenvp** pro **wmain**. Proto je bezpečnější použít pro přístup k informacím o prostředí **_environ** nebo **_wenviron** . Další informace o vztahu **_putenv** a **_wputenv** ke globálním proměnným naleznete v tématu [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Řady funkcí **_putenv** a **_getenv** nejsou bezpečné pro přístup z více vláken. **_getenv** může vracet ukazatel na řetězec, zatímco **_putenv** upravuje řetězec a způsobuje náhodných selhání. Ujistěte se, že jsou volání těchto funkcí synchronizovaná.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku použití **_putenv**naleznete v tématu [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
