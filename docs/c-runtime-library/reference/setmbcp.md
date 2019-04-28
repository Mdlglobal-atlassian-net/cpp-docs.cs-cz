---
title: _setmbcp
ms.date: 11/04/2016
apiname:
- _setmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: c1f4967baa5fda68a7df33bcd08935dca23fab16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62356456"
---
# <a name="setmbcp"></a>_setmbcp

Nastaví nové vícebajtové znakové stránky.

## <a name="syntax"></a>Syntaxe

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parametry

*codepage*<br/>
Nové nastavení stránky kód pro vícebajtové rutiny nezávislý na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud znaková stránka nastavena úspěšně. Pokud není zadána hodnota stránky neplatný kód pro *znakovou stránku, která*, vrátí hodnotu -1 a znakové stránky je beze změny. Nastaví **errno** k **EINVAL** Pokud dojde k selhání přidělení paměti.

## <a name="remarks"></a>Poznámky

**_Setmbcp** funkce určuje nové vícebajtové znakové stránky. Ve výchozím systému za běhu automaticky nastaví je vícebajtová znaková stránka na systému výchozí ANSI znakovou stránku. Vícebajtové znakové stránky ovlivní všechny vícebajtové rutin, které nejsou závislé na národním prostředí. Je ale možná dáte pokyn, aby **_setmbcp** použít znakovou stránku definovaný pro aktuální národní prostředí (viz následující seznam konstant manifestu a související chování výsledků). Seznam vícebajtové rutin, které jsou závislé na znaková stránka národního prostředí namísto vícebajtové znakové stránky najdete v tématu [interpretace vícebajtové znakové sekvence](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Je vícebajtová znaková stránka také ovlivňuje zpracování vícebajtových znaků pomocí následující rutiny knihovny run-time:

||||
|-|-|-|
|[Funkce _exec](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath –](fullpath-wfullpath.md)|[_spawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Kromě toho všechny rutiny knihovny run-time, které přijímají vícebajtového znaku zakončeného *argv* nebo *envp* programu argumenty jako parametry (například **_exec** a **_spawn** rodiny) zpracovat tyto řetězce podle vícebajtové znakové stránky. Proto tyto rutiny jsou také ovlivněny volání **_setmbcp** se mění vícebajtové znakové stránky.

*Znakovou stránku, která* argument můžete nastavit na některou z následujících hodnot:

- **_MB_CP_ANSI** znakovou stránku ANSI použití získané z operačního systému při spuštění programu.

- **_MB_CP_LOCALE** použití aktuálního národního prostředí znakové stránky získané z předchozího volání [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** znakovou stránku OEM použití získané z operačního systému při spuštění programu.

- **_MB_CP_SBCS** použití jednobajtové znakové stránky. Pokud je znaková stránka nastavena na **_MB_CP_SBCS**, rutiny jako [_ismbblead](ismbblead-ismbblead-l.md) vždy vrátí hodnotu false.

- Žádné jiné platné hodnotu znakové stránky, bez ohledu na to, zda je hodnota ANSI, OEM nebo jiných provoz, system, nepodporuje znakovou stránku (s výjimkou UTF-7 a UTF-8, které nejsou podporovány).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
