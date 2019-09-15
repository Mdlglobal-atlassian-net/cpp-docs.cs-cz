---
title: _outp, _outpw, _outpd
ms.date: 11/04/2016
api_name:
- _outpd
- _outp
- _outpw
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
ms.openlocfilehash: d1e7028ae833e1358ce3199b7e7079535c84d135
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944135"
---
# <a name="_outp-_outpw-_outpd"></a>_outp, _outpw, _outpd

Výstupy, na portu, Byte (`_outp`), Word (`_outpw`) nebo Double Word (`_outpd`).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT.

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```

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

#### <a name="parameters"></a>Parametry
*přístavní*<br/>
Číslo portu.

*databyte, dataword*<br/>
Výstupní hodnoty.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí výstup dat. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce `_outp`, `_outpw` a`_outpd` zapisují do zadaného výstupního portu bajt, slovo a Dvojitá slova. Argument *port* může být libovolný unsigned integer v rozsahu 0 – 65 535; *databyte* může být libovolné celé číslo v rozsahu 0-255; a *dataword* může být libovolná hodnota v rozsahu celého čísla, krátké celé číslo bez znaménka a dlouhé celé číslo bez znaménka v uvedeném pořadí.

Vzhledem k tomu, že tyto funkce zapisují přímo do vstupně-výstupního portu, nelze je použít v uživatelském kódu. Informace o používání vstupně-výstupních portů v těchto operačních systémech najdete v tématu "sériová komunikace v systému Win32" na webu MSDN.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_outp`|\<CONIO. h >|
|`_outpw`|\<CONIO. h >|
|`_outpd`|\<CONIO. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
