---
title: _setmbcp
ms.date: 11/04/2016
api_name:
- _setmbcp
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
ms.openlocfilehash: 1db6a83bd864180d513f61cf255bd862283a6cd0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948216"
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

*codepage*<br/>
Nové nastavení znakové stránky pro vícebajtové rutiny nezávislé na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je znaková stránka nastavena úspěšně. Pokud je zadána neplatná hodnota znakové stránky pro *znakovou*stránku, vrátí hodnotu-1 a nastavení znakové stránky zůstane beze změny. Nastaví **errno** na **EINVAL** , pokud dojde k selhání přidělení paměti.

## <a name="remarks"></a>Poznámky

Funkce **_setmbcp** Určuje novou vícebajtovou znakovou stránku. Ve výchozím nastavení systém za běhu automaticky nastaví vícebajtovou znakovou stránku na znakovou stránku ANSI systému výchozí. Nastavení vícebajtových znakových stránek má vliv na všechny vícebajtové rutiny, které nejsou závislé na národním prostředí. Je však možné dát **_setmbcp** pokyn, aby používal znakovou stránku definovanou pro aktuální národní prostředí (viz následující seznam konstant manifestů a přidružených výsledků chování). Seznam vícebajtových rutin, které jsou závislé na znakové stránce národního prostředí, nikoli na vícebajtové znakové stránce, naleznete v tématu [Interpretace vícebajtových znakových sekvencí](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Vícebajtová znaková stránka také ovlivňuje zpracování vícebajtových znaků pomocí následujících rutin knihovny run-time:

||||
|-|-|-|
|[funkce _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[funkce _spawn](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Kromě toho všechny rutiny běhové knihovny, které přijímají vícebajtové znakové *argv* nebo argumenty programu *envp* jako parametry (například **_exec** a **_spawn** ) zpracovávají tyto řetězce podle vícebajtové znakové stránky. Proto jsou tyto rutiny ovlivněny také voláním **_setmbcp** , které mění vícebajtovou znakovou stránku.

Argument *codepage* lze nastavit na některou z následujících hodnot:

- **_MB_CP_ANSI** Použijte znakovou stránku ANSI získanou z operačního systému při spuštění programu.

- **_MB_CP_LOCALE** Použijte znakovou stránku aktuálního národního prostředí získanou z předchozího volání metody [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Použijte znakovou stránku OEM získanou z operačního systému při spuštění programu.

- **_MB_CP_SBCS** Použijte znakovou stránku s jedním bajtem. Když je znaková stránka nastavená na **_MB_CP_SBCS**, rutina jako [_ismbblead](ismbblead-ismbblead-l.md) vždycky vrátí hodnotu false.

- Jakákoli jiná platná hodnota znakové stránky bez ohledu na to, zda je hodnota ANSI, OEM nebo jiná znaková stránka podporovaná operačním systémem (s výjimkou UTF-7 a UTF-8, která není podporována).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmbcp**|\<Mbctype. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
