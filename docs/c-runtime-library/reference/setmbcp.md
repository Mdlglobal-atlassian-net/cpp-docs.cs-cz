---
title: _setmbcp | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e879d4cf6ebc7cb7f61199b3bb52f1a5e3f5389
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
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

*znakové stránky*<br/>
Nové nastavení stránky kód pro vícebajtové rutiny nezávislé na národním prostředí.

## <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu 0, pokud je úspěšně nastavená znaková stránka. Pokud je zadaný hodnotou stránky neplatný kód pro *codepage*, vrátí hodnotu -1 a znakové stránky se nemění. Nastaví **errno** k **einval –** Pokud dojde k chybě přidělení paměti.

## <a name="remarks"></a>Poznámky

**_Setmbcp** funkce určuje nové vícebajtové znakové stránky. Ve výchozím nastavení spuštění systému automaticky nastaví vícebajtové znakové stránky na ANSI výchozí systémová znaková stránka. Vícebajtové znakové stránky ovlivňuje všechny vícebajtové rutin, které nejsou závislé národního prostředí. Je však možné dáte pokyn, aby **_setmbcp** používat znaková stránka definovaný pro aktuální národní prostředí (najdete v následujícím seznamu manifestu konstanty a související chování výsledky). Seznam vícebajtové rutiny, které jsou závislé na znaková stránka národního prostředí, nikoli vícebajtové znakové stránky, naleznete v části [výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Vícebajtové znakové stránky taky ovlivňuje zpracování vícebajtových znaků pomocí následující rutiny běhové knihovny:

||||
|-|-|-|
|[_exec – funkce](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath –](fullpath-wfullpath.md)|[_spawn – funkce](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Kromě toho všechny rutiny běhové knihovny, které přijímají vícebajtových znaků *argv –* nebo *envp –* programu argumenty jako parametry (například **_exec** a **_spawn** rodiny) zpracovat tyto řetězce podle vícebajtové znakové stránky. Proto tyto rutiny jsou také ovlivněné volání **_setmbcp** , změní vícebajtové znakové stránky.

*Codepage* argument může být nastaven na žádný z následujících hodnot:

- **_MB_CP_ANSI** znaková stránka ANSI použití získané z operačního systému při spuštění programu.

- **_MB_CP_LOCALE** použití aktuální národní prostředí znaková stránka získané z předchozího volání [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** znaková stránka OEM použití získané z operačního systému při spuštění programu.

- **_MB_CP_SBCS** použití jednobajtová znaková stránka. Pokud se nastaví znaková stránka **_MB_CP_SBCS**, rutiny jako [_ismbblead –](ismbblead-ismbblead-l.md) vždy vrátí hodnotu false.

- Žádné jiné platné hodnotu znakové stránky, bez ohledu na to, zda je hodnota ANSI, OEM nebo jiné operační systém – podporované znakové stránky (s výjimkou znakové sady UTF-7 a UTF-8, které nejsou podporovány).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_setmbcp**|\<Mbctype.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
