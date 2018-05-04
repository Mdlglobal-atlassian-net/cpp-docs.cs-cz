---
title: _putenv_s –, _wputenv_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
dev_langs:
- C++
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e84d7a68530a748c9b1ad7c553fad80ed4e7c86b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="putenvs-wputenvs"></a>_putenv_s, _wputenv_s

Vytvoří, upraví nebo odstraní proměnné prostředí. Toto jsou verze [_putenv –, _wputenv –](putenv-wputenv.md) , ale mají vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Hodnota k nastavení proměnné prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud bylo úspěšné, nebo chybový kód.

### <a name="error-conditions"></a>Chybové stavy

|*název_proměnné*|*value_string*|Návratová hodnota|
|------------|-------------|------------------|
|**HODNOTU NULL**|všechny|**EINVAL –**|
|všechny|**HODNOTU NULL**|**EINVAL –**|

Pokud nenastane některá z chybových stavech tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **einval –** a nastavte **errno** k **einval –**.

## <a name="remarks"></a>Poznámky

**_Putenv_s –** funkce přidá nové proměnné prostředí nebo upraví hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém proces provádí (například výchozí cesta hledání pro knihovny propojení v aplikaci). **_wputenv_s –** je verze široká charakterová **_putenv_s –**; *envstring* argument **_wputenv_s –** je široká charakterová řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*název_proměnné* je název proměnné prostředí, chcete-li přidat nebo upravit a *value_string* je hodnota proměnné. Pokud *název_proměnné* už je součástí prostředí, jeho hodnota je nahrazena *value_string*, jinak nový *název_proměnné* proměnnou a její *value_string*  se přidají do prostředí. Proměnnou z prostředí můžete odebrat tak, že zadáte prázdný řetězec (to znamená, "") pro *value_string*.

**_putenv_s –** a **_wputenv_s –** ovlivňují jenom prostředí, ve kterém je lokální vzhledem k aktuální proces; se nedá použít k úpravě prostředí příkaz úrovni. Tyto funkce fungují pouze na datové struktury, které jsou k dispozici běhové knihovny a ne na prostředí "segment", který vytvoří operační systém pro zpracování. Aktuální proces ukončí, stane se prostředí úroveň volání procesu, který se ve většině případů je úroveň operačního systému. Změny prostředí však lze předat všechny nové procesy, které jsou vytvořené pomocí **_spawn**, **_exec**, nebo **systému**, a získat všechny nové položky, které jsou tyto nové procesy přidal **_putenv_s –** a **_wputenv_s –**.

Neměňte položku prostředí přímo. Místo toho použijte **_putenv_s –** nebo **_wputenv_s –** ho změnit. Na konkrétní prvky uvolnění přímo **[] _environ –** globální pole může způsobit neplatná paměti vzít v úvahu.

**GETENV –** a **_putenv_s –** pomocí globální proměnné **_environ –** pro přístup k tabulce prostředí; **_wgetenv –** a **_wputenv_s –** použít **_wenviron –**. **_putenv_s –** a **_wputenv_s –** může změnit hodnotu **_environ –** a **_wenviron –**a tím zneplatnit *envp –*argument **hlavní** a **_wenvp** argument **wmain**. Proto je bezpečnější používat **_environ –** nebo **_wenviron –** pro přístup k informacím prostředí. Další informace o vztah **_putenv_s –** a **_wputenv_s –** globální proměnné, najdete v tématu [_environ –, _wenviron –](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv_s –** a **_getenv_s** řady funkcí nejsou bezpečné pro přístup z více vláken. **_getenv_s** může vrátit ukazatel řetězec při **_putenv_s –** je úprava řetězec a tím způsobit náhodné chyby. Ujistěte se, že jsou synchronizovány volání na tyto funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad, který ukazuje způsob použití **_putenv_s –**, najdete v části [getenv_s –, _wgetenv_s –](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
