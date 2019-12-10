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
ms.openlocfilehash: 48e0e58d2886c5a8bb90a86c81cb785d364666e8
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988710"
---
# <a name="inp-_inp-inpw-_inpw-_inpd"></a>INP, _inp, inpw, _inpw, _inpd

Vstupy, z portu, bajt (`inp`, `_inp`), slovo (`inpw`, `_inpw`) nebo dvojité slovo (`_inpd`).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT.  
> Toto API nelze použít v aplikacích, které jsou spuštěny v modulu Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

\ *portu*
Číslo portu I/O.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí byte, word nebo double word přečtený z `port`. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

Funkce `_inp`, `_inpw` a `_inpd` přečtou byte, word, resp. double word ze zadaného vstupního portu. Vstupní hodnota může být jakékoli krátké celé číslo bez znaménka v rozsahu 0-65 535.

Vzhledem k tomu, že tyto funkce jsou čteny přímo z portu I/O, nelze je použít v uživatelském kódu.

Názvy `inp` a `inpw` jsou starší, zastaralé názvy pro `_inp` a `_inpw` funkce. Další informace najdete v tématu [názvy funkcí POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_inp`|\<CONIO. h >|
|`_inpw`|\<CONIO. h >|
|`_inpd`|\<CONIO. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[I/O\ konzoly a portu](../c-runtime-library/console-and-port-i-o.md)
[outp, outpw, _outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
