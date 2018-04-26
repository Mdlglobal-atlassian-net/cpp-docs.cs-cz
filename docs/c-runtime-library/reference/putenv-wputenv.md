---
title: _putenv –, _wputenv – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _putenv
- _wputenv
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
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
dev_langs:
- C++
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
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 74984106c94ec3b6af1811fba63707d7d5056791
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv

Vytvoří, upraví nebo odstraní proměnné prostředí. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_putenv_s –, _wputenv_s –](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
Definice řetězců prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí 0, pokud bylo úspěšné nebo -1 v případě k chybě.

## <a name="remarks"></a>Poznámky

**_Putenv –** funkce přidá nové proměnné prostředí nebo upraví hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém proces provádí (například výchozí cesta hledání pro knihovny propojení v aplikaci). **_wputenv –** je verze široká charakterová **_putenv –**; *envstring* argument **_wputenv –** je široká charakterová řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv –**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring* argument musí být ukazatel na řetězec ve formátu *název_proměnné*=*value_string*, kde *název_proměnné* je Název proměnné prostředí, chcete-li přidat nebo upravit a *value_string* je hodnota proměnné. Pokud *název_proměnné* už je součástí prostředí, jeho hodnota je nahrazena *value_string*, jinak nový *název_proměnné* proměnnou a její *value_string*  hodnota se přidá do prostředí. Proměnnou z prostředí můžete odebrat tak, že zadáte prázdnou *value_string*, nebo jinými slovy, tak, že zadáte pouze *název_proměnné*=.

**_putenv –** a **_wputenv –** ovlivňují jenom prostředí, ve kterém je lokální vzhledem k aktuální proces; se nedá použít k úpravě prostředí příkaz úrovni. To znamená tyto funkce fungují pouze na datové struktury přístupné běhové knihovny a ne na prostředí segmentu pro proces vytvořené operačního systému. Aktuální proces ukončí, stane se prostředí úroveň proces volání (ve většině případů úroveň operačního systému). Ale upravený prostředí se dá předat do jakékoli nové procesů vytvořených službou **_spawn**, **_exec**, nebo **systému**, a získat tyto nové procesy žádné nové položky přidal **_putenv –** a **_wputenv –**.

Neměňte položku prostředí přímo: místo toho použijte **_putenv –** nebo **_wputenv –** ho změnit. Na konkrétní prvky uvolnění přímo **[] _environ –** globální pole může vést k neplatné paměti adresovaném.

**GETENV –** a **_putenv –** pomocí globální proměnné **_environ –** pro přístup k tabulce prostředí; **_wgetenv –** a **_wputenv –** použít **_wenviron –**. **_putenv –** a **_wputenv –** může změnit hodnotu **_environ –** a **_wenviron –**, proto zrušení platnosti **_envp** argument **hlavní** a **_wenvp** argument **wmain**. Proto je bezpečnější používat **_environ –** nebo **_wenviron –** pro přístup k informacím prostředí. Další informace o vztahu z **_putenv –** a **_wputenv –** globální proměnné, najdete v tématu [_environ –, _wenviron –](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv –** a **_getenv** řady funkcí nejsou bezpečné pro přístup z více vláken. **_getenv** může vrátit ukazatel řetězec při **_putenv –** upravuje řetězec, způsobuje náhodné chyby. Ujistěte se, že jsou synchronizovány volání na tyto funkce.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Příklad, jak pomocí **_putenv –**, najdete v části [getenv _wgetenv –](getenv-wgetenv.md).

## <a name="see-also"></a>Viz také

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
