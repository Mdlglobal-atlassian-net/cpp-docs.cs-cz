---
title: outp, outpw, _outp, _outpw, _outpd
description: Popisuje zastaralé a odebrané funkce outp, outpw, _outp, _outpw a _outpd v knihovně CRT (Microsoft C Runtime Library).
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 3d0342ae94276c7875bcb737b0d1a64aabafd235
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825925"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp, outpw, _outp, _outpw, _outpd

Výstupy, na portu,`outp`bajt (, `_outp`), slovo (`outpw`, `_outpw`) nebo dvojité slovo (`_outpd`).

> [!IMPORTANT]
> Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT. \
> Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>Parametry

*přístavní*\
Číslo portu.

*databyte, dataword*\
Výstupní hodnoty.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí výstup dat. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce `_outp`, `_outpw`a `_outpd` zapisují do zadaného výstupního portu bajt, slovo a Dvojitá slova. Argument *port* může být libovolný unsigned integer v rozsahu 0 – 65 535; *databyte* může být libovolné celé číslo v rozsahu 0-255; a *dataword* může být libovolná hodnota v rozsahu celého čísla, krátké celé číslo bez znaménka a dlouhé celé číslo bez znaménka v uvedeném pořadí.

Vzhledem k tomu, že tyto funkce zapisují přímo do vstupně-výstupního portu, nelze je použít v uživatelském kódu. Informace o používání vstupně-výstupních portů v těchto operačních systémech najdete v tématu "sériová komunikace v systému Win32" na webu MSDN.

Názvy `outp` a `outpw` jsou starší, zastaralé názvy pro funkce `_outp` a. `_outpw` Další informace najdete v tématu [názvy funkcí POSIX](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_outp`|\<CONIO. h>|
|`_outpw`|\<CONIO. h>|
|`_outpd`|\<CONIO. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)\
[INP, inpw, _inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
