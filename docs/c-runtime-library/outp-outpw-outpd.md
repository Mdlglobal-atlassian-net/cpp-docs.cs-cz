---
title: _outp, _outpw, _outpd
ms.date: 11/04/2016
apiname:
- _outpd
- _outp
- _outpw
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
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
ms.openlocfilehash: 1a507f4115a48372706590eb61f9e3e77a0e3548
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57752061"
---
# <a name="outp-outpw-outpd"></a>_outp, _outpw, _outpd

Výstupy, na portu, byte (`_outp`), word (`_outpw`), nebo double word (`_outpd`).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od v sadě Visual Studio 2015, nejsou k dispozici v CRT.

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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
*Port*<br/>
Číslo portu.

*databyte dataword*<br/>
Výstupní hodnoty.

## <a name="return-value"></a>Návratová hodnota

Funkce vrací datový výstup. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

`_outp`, `_outpw`, A `_outpd` funkce zapisují byte, word a double word, resp. do zadaného výstupního portu. *Port* argument může být libovolné celé číslo bez znaménka v rozsahu 0 – 65 535; *databyte* může být libovolné celé číslo v rozsahu 0 – 255 a *dataword* může být libovolná hodnota v rozsahu celého čísla, krátké celé číslo bez znaménka a celé číslo bez znaménka dlouhý, v uvedeném pořadí.

Vzhledem k tomu, že tyto funkce zapisují přímo do portu I/O, nemohou být použity v uživatelském kódu. Informace o použití I/O portů v těchto operačních systémů vyhledání "Sériové komunikace ve Win32" na webu MSDN.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také:

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_inp, _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
