---
title: _putenv, _wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: a86b58b868c96b6f77af8bfa32036d1a56b2a7cf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918859"
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

Funkce **_putenv** přidá nové proměnné prostředí nebo upraví hodnoty stávajících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spouští (například výchozí cesta pro hledání knihoven, které mají být propojeny s programem). **_wputenv** je verze **_putenv**s velkým znakem; Argument *envstring* pro **_wputenv** je řetězec s velkým znakem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Argument *envstring* musí být ukazatel na řetězec ve formě *název_proměnné*=*value_string*, kde *název_proměnné* je název proměnné prostředí, která se má přidat nebo upravit a *value_string* je hodnota proměnné. Pokud je hodnota *název_proměnné* již součástí prostředí, je její hodnota nahrazena *value_string*; v opačném případě se nová proměnná *název_proměnné* a její *value_string* hodnota přidá do prostředí. Proměnnou můžete z prostředí odebrat zadáním prázdné *value_string*nebo jinými slovy zadáním pouze *název_proměnné*=.

**_putenv** a **_wputenv** ovlivňují pouze prostředí, které je pro aktuální proces místní. nelze je použít pro úpravu prostředí na úrovni příkazu. To znamená, že tyto funkce pracují pouze s datovými strukturami dostupnými pro běhovou knihovnu a nikoli s segmentem prostředí vytvořeným pro proces operačním systémem. Po ukončení aktuálního procesu se prostředí vrátí na úroveň volajícího procesu (ve většině případů na úrovni operačního systému). Upravené prostředí je ale možné předat všem novým procesům vytvořeným **_spawn**, **_execm**nebo **systémem**a tyto nové procesy získají všechny nové položky přidané **_putenv** a **_wputenv**.

Neměňte položku prostředí přímo: místo toho použijte **_putenv** nebo **_wputenv** pro jejich změnu. Konkrétně přímé uvolnění prvků **_environ []** globální pole může vést k adresování neplatné paměti.

**getenv** a **_putenv** použít globální proměnnou **_environ** pro přístup k tabulce prostředí; **_wgetenv** a **_wputenv** používají **_wenviron**. **_putenv** a **_wputenv** mohou změnit hodnotu **_environ** a **_wenviron**, čímž se neověřuje argument **_envp** **Main** a argument **_wenvp** pro **wmain**. Proto je bezpečnější použít pro přístup k informacím o prostředí **_environ** nebo **_wenviron** . Další informace o vztahu **_putenv** a **_wputenv** globálním proměnným naleznete v tématu [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv** a **_getenv** rodin funkcí nejsou bezpečné pro přístup z více vláken. **_getenv** může vracet ukazatel na řetězec, zatímco **_putenv** upravuje řetězec, což způsobuje náhodné selhání. Ujistěte se, že jsou volání těchto funkcí synchronizovaná.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv**|\<Stdlib. h>|
|**_wputenv**|\<Stdlib. h> nebo \<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku použití **_putenv**naleznete v tématu [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
