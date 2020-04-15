---
title: _putenv_s, _wputenv_s
ms.date: 4/2/2020
api_name:
- _wputenv_s
- _putenv_s
- _o__putenv_s
- _o__wputenv_s
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
ms.openlocfilehash: f0164feed05b409ba29ca713f11f4f3323dbaac3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338394"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Vytvoří, upraví nebo odebere proměnné prostředí. Jedná se o verze [_putenv, _wputenv](putenv-wputenv.md) ale mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*název var*<br/>
Název proměnné prostředí.

*value_string*<br/>
Hodnota pro nastavení proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšná, nebo kód chyby.

### <a name="error-conditions"></a>Chybové stavy

|*název var*|*value_string*|Návratová hodnota|
|------------|-------------|------------------|
|**Null**|jakékoli|**EINVAL**|
|jakékoli|**Null**|**EINVAL**|

Pokud dojde k jednomu z chybových stavů, tyto funkce vyvolat neplatný obslužnou rutinu parametru, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, tyto funkce vrátí **EINVAL** a nastavit **errno** na **EINVAL**.

## <a name="remarks"></a>Poznámky

Funkce **_putenv_s** přidává nové proměnné prostředí nebo upravuje hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spouští (například výchozí vyhledávací cesta pro knihovny, které mají být propojeny s programem). **_wputenv_s** je širokoznaková verze **_putenv_s**; *envstring* argument **_wputenv_s** je řetězec s širokým znakem.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definováno|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* je název proměnné prostředí, která má být přidána nebo změněna a *value_string* je hodnota proměnné. Pokud *je název var* již součástí prostředí, jeho hodnota se nahradí *value_string*; v opačném případě jsou do prostředí přidány nové proměnné *varname* a její *value_string.* Proměnnou můžete odebrat z prostředí zadáním prázdného řetězce (tj. "") pro *value_string*.

**_putenv_s** a **_wputenv_s** ovlivnit pouze prostředí, které je místní aktuální proces; nelze je použít k úpravě prostředí na úrovni příkazu. Tyto funkce pracují pouze na datových strukturách, které jsou přístupné pro knihovnu za běhu a nikoli v "segmentu" prostředí, který operační systém vytvoří pro proces. Po ukončení aktuálního procesu se prostředí vrátí na úroveň volajícího procesu, což je ve většině případů úroveň operačního systému. Upravené prostředí však může být předáno všem novým procesům, které jsou vytvořeny **_spawn**, **_exec**nebo **systémem**, a tyto nové procesy získají všechny nové položky, které jsou přidány **_putenv_s** a **_wputenv_s**.

Neměňte přímo položku prostředí. místo toho jej změňte **pomocí _putenv_s** nebo **_wputenv_s.** Zejména přímé uvolnění prvků **_environ[]** globální pole může způsobit neplatné paměti, které mají být vyřešeny.

**getenv** a **_putenv_s** používají globální proměnnou **_environ** pro přístup k tabulce prostředí; **_wgetenv** a **_wputenv_s** používat **_wenviron**. **_putenv_s** a **_wputenv_s** může změnit hodnotu **_environ** a **_wenviron**, a tím zneplatnit argument *envp* na **main** a **_wenvp** argument **wmain**. Proto je bezpečnější používat **_environ** nebo **_wenviron** pro přístup k informacím o prostředí. Další informace o vztahu **_putenv_s** a **_wputenv_s** ke globálním proměnným naleznete [v tématu _environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **Rodiny funkcí _putenv_s** a **_getenv_s** nejsou bezpečné pro přístup z více vláken. **_getenv_s** může vrátit ukazatel řetězce, zatímco **_putenv_s** upravuje řetězec, a tím způsobit náhodné chyby. Ujistěte se, že volání těchto funkcí jsou synchronizovány.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> \<nebo wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Ukázka, která ukazuje, jak používat **_putenv_s**, najdete [v tématu getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
