---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
apiname:
- _wputenv_s
- _putenv_s
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
ms.openlocfilehash: f675c2c0a2b12db3cce841dd0db9fa722393f1b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50558948"
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Vytvoří, změní nebo odebere proměnné prostředí. Jde o verzích [_putenv _wputenv](putenv-wputenv.md) ale mají rozšíření zabezpečení popsaná v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Název proměnné prostředí.

*value_string*<br/>
Hodnota k nastavení proměnné prostředí pro.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná, nebo kód chyby.

### <a name="error-conditions"></a>Chybové podmínky

|*název_proměnné*|*value_string*|Návratová hodnota|
|------------|-------------|------------------|
|**HODNOTU NULL**|Všechny|**EINVAL**|
|Všechny|**HODNOTU NULL**|**EINVAL**|

Pokud nenastane některá z chybových stavů, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastavte **errno** k **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Putenv_s** funkce přidává nové proměnné prostředí nebo upravuje hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spustí (například výchozí cesta pro vyhledávání pro knihovny, které chcete propojit s programem). **_wputenv_s –** je verze širokého znaku **_putenv_s**; *envstring* argument **_wputenv_s –** je širokoznaký řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE a _MBCS nejsou definovány|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*název_proměnné* je název proměnné prostředí, která se přidá nebo upraví a *value_string* je hodnota proměnné. Pokud *název_proměnné* je již součástí životního prostředí, její hodnota je nahrazena *value_string*; v opačném případě nová *název_proměnné* proměnnou a její *value_string*  jsou přidány do prostředí. Proměnnou můžete odebrat z prostředí zadáním prázdného řetězce (tedy "") pro *value_string*.

**_putenv_s** a **_wputenv_s –** vliv jenom prostředí, které je místní pro aktuální proces; nelze je použít ke změně úrovně příkazového prostředí. Tyto funkce pracují pouze na datové struktury, které jsou k dispozici ke knihovně runtime a ne na "segmentu, který operační systém vytvoří proces prostředí. Když skončí aktuální proces, prostředí se vrátí na úroveň volajícího procesu, který ve většině případů je úroveň operačního systému. Upravené prostředí však lze předat do všech nových procesů, které jsou vytvořeny pomocí **_spawn**, **_exec**, nebo **systému**, a tyto nové procesy budou mít všechny nové položky, které jsou přidal **_putenv_s** a **_wputenv_s –**.

Neměňte položku prostředí přímo. Místo toho použijte **_putenv_s** nebo **_wputenv_s –** ho změnit. Konkrétně se přímo uvolňování prvků **[] _environ** globální pole může dojít k adresování neplatné paměti.

**GETENV** a **_putenv_s** pomocí globální proměnné **_environ** pro přístup k tabulce prostředí. **_wgetenv** a **_wputenv_s –** použít **_wenviron**. **_putenv_s** a **_wputenv_s –** může změnit hodnotu **_environ** a **_wenviron**a tím zneplatnit *envp*argument **hlavní** a **_wenvp** argument **wmain**. Proto je bezpečnější používat **_environ** nebo **_wenviron** pro přístup k informacím o prostředí. Další informace o vztah mezi **_putenv_s** a **_wputenv_s –** ke globálním proměnným viz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s** a **_getenv_s** rodinách funkcí nejsou vláknově bezpečné. **_getenv_s** může vrátit ukazatel řetězce při **_putenv_s** se upravuje řetězec a tím způsobí náhodná selhání. Ujistěte se, že volání těchto funkcí jsou synchronizována.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad, který ukazuje způsob použití **_putenv_s**, naleznete v tématu [getenv_s – _wgetenv_s –](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
