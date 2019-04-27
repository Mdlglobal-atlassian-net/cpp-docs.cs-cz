---
title: _putenv, _wputenv
ms.date: 11/04/2016
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
ms.openlocfilehash: 952a4d62f6ceb6b689091ac09f6ca338d0b10864
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62357884"
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv

Vytvoří, změní nebo odebere proměnné prostředí. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [_putenv_s _wputenv_s –](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

Vrátit 0 v případě úspěchu nebo -1 v případě chyby.

## <a name="remarks"></a>Poznámky

**_Putenv** funkce přidává nové proměnné prostředí nebo upravuje hodnoty existujících proměnných prostředí. Proměnné prostředí definují prostředí, ve kterém se proces spustí (například výchozí cesta pro vyhledávání pro knihovny, které chcete propojit s programem). **_wputenv** je verze širokého znaku **_putenv**; *envstring* argument **_wputenv** je širokoznaký řetězec.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring* argument musí být ukazatel na řetězec ve formě *název_proměnné*=*value_string*, kde *název_proměnné* je Název proměnné prostředí, která se přidá nebo upraví a *value_string* je hodnota proměnné. Pokud *název_proměnné* je již součástí životního prostředí, její hodnota je nahrazena *value_string*; v opačném případě nová *název_proměnné* proměnnou a její *value_string*  hodnoty jsou přidány do prostředí. Proměnnou můžete odebrat z prostředí zadáním prázdného *value_string*, nebo jinými slovy, zadáním pouze *název_proměnné*=.

**_putenv** a **_wputenv** vliv jenom prostředí, které je místní pro aktuální proces; nelze je použít ke změně úrovně příkazového prostředí. To znamená, že tyto funkce pracují pouze na datových strukturách dostupných knihovně runtime a ne na segmentu prostředí vytvořeném pro proces operačním systémem. Když skončí aktuální proces, prostředí se vrátí na úroveň volajícího procesu (ve většině případů úroveň operačního systému). Upravené prostředí však mohou být předány do všech nových procesů vytvořených službou **_spawn**, **_exec**, nebo **systému**, a tyto nové procesy budou mít všechny nové položky přidané **_putenv** a **_wputenv**.

Neměňte položku prostředí přímo: místo toho použijte **_putenv** nebo **_wputenv** ho změnit. Zejména přímé uvolňování prvků **[] _environ** globální pole, které by mohly vést k adresování neplatné paměti.

**GETENV** a **_putenv** pomocí globální proměnné **_environ** pro přístup k tabulce prostředí. **_wgetenv** a **_wputenv** použít **_wenviron**. **_putenv** a **_wputenv** může změnit hodnotu **_environ** a **_wenviron**, a zrušit tak platnost **_envp** argument **hlavní** a **_wenvp** argument **wmain**. Proto je bezpečnější používat **_environ** nebo **_wenviron** pro přístup k informacím o prostředí. Další informace o vztahu **_putenv** a **_wputenv** ke globálním proměnným viz [_environ _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> **_Putenv** a **_getenv** rodinách funkcí nejsou vláknově bezpečné. **_getenv** může vrátit ukazatel řetězce při **_putenv** upravuje řetězec, což způsobí náhodná selhání. Ujistěte se, že volání těchto funkcí jsou synchronizována.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h > nebo \<wchar.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Pro ukázku toho, jak používat **_putenv**, naleznete v tématu [getenv _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Viz také:

[Řízení procesů a prostředí](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
