---
title: INP, _inp, inpw, _inpw, _inpd
description: Popisuje zastaralé a odebrané funkce INP, _inp, inpw, _inpw a _inpd v knihovně CRT (Microsoft C Runtime Library).
ms.date: 12/09/2019
api_name:
- inp
- inpw
- _inp
- _inpw
- _inpd
api_location:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- inp
- inpw
- _inp
- _inpw
- _inpd
helpviewer_keywords:
- inp function
- inpw function
- ports, I/O routines
- inpd function
- _inp function
- _inpd function
- I/O [CRT], port
- _inpw function
ms.assetid: 5d9c2e38-fc85-4294-86d5-7282cc02d1b3
ms.openlocfilehash: f7b822c4b694969407e32ba26026465fb39bd8d6
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825826"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Vstupy, z portu,`inp`Byte (, `_inp`), slovo (`inpw`, `_inpw`) nebo Double Word (`_inpd`).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT. \
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```cpp
int _inp(
   unsigned short port
);
unsigned short _inpw(
   unsigned short port
);
unsigned long _inpd(
   unsigned short port
);
```

### <a name="parameters"></a>Parametry

*přístavní*\
Číslo portu I/O.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí bajt, slovo nebo Double Word čtený z `port`. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce `_inp`, `_inpw`a `_inpd` čtou v zadaném vstupním portu bajt, slovo a dvojité slovo. Vstupní hodnota může být jakékoli krátké celé číslo bez znaménka v rozsahu 0-65 535.

Vzhledem k tomu, že tyto funkce jsou čteny přímo z portu I/O, nelze je použít v uživatelském kódu.

Názvy `inp` a `inpw` jsou starší, zastaralé názvy pro funkce `_inp` a. `_inpw` Další informace najdete v tématu [názvy funkcí POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_inp`|\<CONIO. h>|
|`_inpw`|\<CONIO. h>|
|`_inpd`|\<CONIO. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)\
[outp, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
