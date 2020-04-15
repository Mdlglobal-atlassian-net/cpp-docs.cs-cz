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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333033"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

Vytvoří, upraví nebo odebere proměnné prostředí. K dispozici jsou bezpečnější verze těchto funkcí. viz [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

V případě chyby vrátíte 0 nebo -1.

## <a name="remarks"></a>Poznámky

Funkce **_putenv** přidá nové proměnné prostředí nebo upraví hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spouští (například výchozí vyhledávací cesta pro knihovny, které mají být propojeny s programem). **_wputenv** je širokoznaková verze **_putenv**; *envstring* argument **_wputenv** je řetězec s širokým znakem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

Argument *envstring* musí být ukazatelem na řetězec názvu *varname*=formuláře*value_string*, kde *varname* je název proměnné prostředí, která má být přidána nebo změněna, a *value_string* je hodnota proměnné. Pokud *je název var* již součástí prostředí, jeho hodnota se nahradí *value_string*; v opačném případě jsou do prostředí přidány nové proměnné *varname* a její *value_string* hodnota. Proměnnou můžete odebrat z prostředí zadáním prázdné *value_string*nebo jinými slovy zadáním pouze *názvu var =.*

**_putenv** a **_wputenv** ovlivnit pouze prostředí, které je místní aktuální proces; nelze je použít k úpravě prostředí na úrovni příkazu. To znamená, že tyto funkce fungují pouze na datových strukturách přístupných pro knihovnu za běhu a nikoli v segmentu prostředí vytvořeném pro proces operačním systémem. Po ukončení aktuálního procesu se prostředí vrátí na úroveň volajícího procesu (ve většině případů úroveň operačního systému). Upravené prostředí však může být předáno všem novým procesům vytvořeným **_spawn**, **_exec**nebo **systémem**a tyto nové procesy získají všechny nové položky přidané **_putenv** a **_wputenv**.

Neměňte položku prostředí přímo: místo toho ji změňte **pomocí _putenv** nebo **_wputenv.** Zejména přímé uvolnění prvky **_environ[]** globální pole může vést k neplatné paměti je určena.

**getenv** a **_putenv** používat globální proměnnou **_environ** pro přístup k tabulce prostředí; **_wgetenv** a **_wputenv** používají **_wenviron**. **_putenv** a **_wputenv** mohou změnit hodnotu **_environ** a **_wenviron**, čímž se zneplatní argument **_envp** na **hlavní** a **_wenvp** argument **na wmain**. Proto je bezpečnější používat **_environ** nebo **_wenviron** pro přístup k informacím o prostředí. Další informace o vztahu **_putenv** a **_wputenv** ke globálním proměnným naleznete [v tématu _environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **Rodiny funkcí _putenv** a **_getenv** nejsou bezpečné pro přístup z více vláken. **_getenv** může vrátit ukazatel řetězce, zatímco **_putenv** upravuje řetězec, což způsobuje náhodné selhání. Ujistěte se, že volání těchto funkcí jsou synchronizovány.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázka použití **_putenv**naleznete v [tématu getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
