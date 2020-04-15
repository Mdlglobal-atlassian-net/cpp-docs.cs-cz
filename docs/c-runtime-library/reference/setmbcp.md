---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337594"
---
# <a name="_setmbcp"></a>_setmbcp

Nastaví novou vícebajtovou znakovou stránku.

## <a name="syntax"></a>Syntaxe

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*Codepage*<br/>
Nové nastavení znakové stránky pro vícebajtové rutiny nezávislé na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je znaková stránka úspěšně nastavena. Pokud je pro *znakovou stránku*zadána neplatná hodnota znakové stránky , vrátí hodnotu -1 a nastavení znakové stránky se nezmění. Nastaví **errno** na **EINVAL,** pokud dojde k chybě přidělení paměti.

## <a name="remarks"></a>Poznámky

Funkce **_setmbcp** určuje novou vícebajtovou znakovou stránku. Ve výchozím nastavení systém run-time automaticky nastaví vícebajtovou znakovou stránku na výchozí kódovou stránku ANSI v systému. Vícebajtové nastavení znakové stránky ovlivňuje všechny vícebajtové rutiny, které nejsou závislé na národním prostředí. Je však možné dát **pokyn _setmbcp** použít znakovou stránku definovanou pro aktuální národní prostředí (viz následující seznam konstant manifestu a souvisejících výsledků chování). Seznam vícebajtových rutin, které jsou závislé na znakové stránce národního prostředí, nikoli na znakové stránce vícebajtů, naleznete [v tématu Interpretace vícebajtových sekvencí znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Vícebajtová znaková stránka také ovlivňuje vícebajtové zpracování znaků pomocí následujících rutin knihovny za běhu:

||||
|-|-|-|
|[_exec funkce](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn funkce](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam řekl:](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Kromě toho všechny rutiny knihovny run-time, které přijímají vícebajtové *argumenty argv* nebo *envp* programu jako parametry (například **_exec** a **_spawn** rodiny) zpracovávají tyto řetězce podle vícebajtové znakové stránky. Proto tyto rutiny jsou také ovlivněny volání **_setmbcp,** která změní vícebajtovou znakovou stránku.

Argument *znakové stránky* lze nastavit na některou z následujících hodnot:

- **_MB_CP_ANSI** Použijte znakovou stránku ANSI získanou z operačního systému při spuštění programu.

- **_MB_CP_LOCALE** Použijte kódovou stránku aktuálního národního prostředí získanou z předchozího volání [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Použijte znakovou stránku výrobce OEM získanou z operačního systému při spuštění programu.

- **_MB_CP_SBCS** Použijte jednobajtou znakovou stránku. Pokud je znaková stránka nastavena na **_MB_CP_SBCS**, rutina, například [_ismbblead](ismbblead-ismbblead-l.md) vždy vrátí false.

- **_MB_CP_UTF8** Použijte UTF-8.  Pokud je znaková stránka nastavena na **_MB_CP_UTF8**, rutina, jako je [například _ismbblead](ismbblead-ismbblead-l.md) vždy vrátí false.

- Jakákoli jiná platná hodnota znakové stránky, bez ohledu na to, zda je hodnota ansi, OEM nebo jiné znakové stránky podporované operačním systémem (s výjimkou UTF-7, která není podporována).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
