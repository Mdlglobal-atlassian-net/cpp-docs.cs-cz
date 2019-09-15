---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
api_name:
- _wputenv_s
- _putenv_s
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
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: b2de609314a12f626a21680b470bc8831eada2cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949903"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Vytvoří, změní nebo odebere proměnné prostředí. Jedná se o verze [_putenv, _wputenv,](putenv-wputenv.md) ale mají vylepšení zabezpečení, jak je popsáno v [části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Parametry

*název_proměnné*<br/>
Název proměnné prostředí

*value_string*<br/>
Hodnota, na kterou má být proměnná prostředí nastavena.

## <a name="return-value"></a>Návratová hodnota

Vrátí 0, pokud bylo úspěšné, nebo kód chyby.

### <a name="error-conditions"></a>Chybové stavy

|*název_proměnné*|*value_string*|Návratová hodnota|
|------------|-------------|------------------|
|**NULL**|Jakýmikoli|**EINVAL**|
|Jakýmikoli|**NULL**|**EINVAL**|

Pokud dojde k jedné z chybových podmínek, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastaví **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_putenv_s** přidá nové proměnné prostředí nebo upraví hodnoty stávajících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spouští (například výchozí cesta pro hledání knihoven, které mají být propojeny s programem). **_wputenv_s** je **_putenv_s**verze s velkým znakem; Argument *envstring* pro **_wputenv_s** je řetězec s velkým znakem.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*název_proměnné* je název proměnné prostředí, která se má přidat nebo upravit a *value_string* je hodnota proměnné. Pokud je hodnota *název_proměnné* již součástí prostředí, je její hodnota nahrazena hodnotou *value_string*; v opačném případě se nová proměnná *název_proměnné* a její *value_string* přidají do prostředí. Proměnnou můžete z prostředí odebrat zadáním prázdného řetězce (tj. "") pro *value_string*.

**_putenv_s** a **_wputenv_s** ovlivňují jenom prostředí, které je pro aktuální proces místní. nelze je použít pro úpravu prostředí na úrovni příkazu. Tyto funkce fungují pouze v datových strukturách, které jsou přístupné pro běhovou knihovnu, nikoli v prostředí segment, které operační systém vytvoří pro proces. Po ukončení aktuálního procesu se prostředí vrátí do úrovně volajícího procesu, který je ve většině případů na úrovni operačního systému. Upravené prostředí však lze předat všem novým procesům vytvořeným pomocí **_spawn**, **_exec**nebo **systému**a tyto nové procesy získají všechny nové položky, které jsou přidány pomocí **_putenv_s** a **_wputenv_s**.

Neměňte položku prostředí přímo; místo toho ho můžete změnit pomocí **_putenv_s** nebo **_wputenv_s** . Konkrétně přímé uvolnění prvků globálního pole **_environ []** může způsobit adresování neplatné paměti.

**getenv** a **_putenv_s** používají globální proměnnou **_environ** pro přístup k tabulce prostředí; **_wgetenv** a **_wputenv_s** používají **_wenviron**. **_putenv_s** a **_wputenv_s** mohou změnit hodnotu **_environ** a **_wenviron**, čímž se neověří argument *envp* **Main** a argument **_wenvp** pro **wmain**. Proto je bezpečnější použít pro přístup k informacím o prostředí **_environ** nebo **_wenviron** . Další informace o vztahu **_putenv_s** a **_wputenv_s** ke globálním proměnným naleznete v tématu [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Řady funkcí **_putenv_s** a **_getenv_s** nejsou bezpečné pro přístup z více vláken. **_getenv_s** by mohl vracet ukazatel na řetězec, zatímco **_putenv_s** upravuje řetězec, a proto způsobují náhodné chyby. Ujistěte se, že jsou volání těchto funkcí synchronizovaná.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<Stdlib. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázku, která ukazuje, jak používat **_putenv_s**, naleznete v tématu [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
