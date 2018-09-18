---
title: _inp – _inpw –, _inpd – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _inp
- _inpw
- _inpd
apilocation:
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- inpd
- _inp
- _inpw
- _inpd
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23e3f28ddb96bb34b38b3dd90ff6720edb1d9224
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041347"
---
# <a name="inp-inpw-inpd"></a>_inp, _inpw, _inpd

Vstupy, z portu, byte (`_inp`), word (`_inpw`), nebo double word (`_inpd`).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od v sadě Visual Studio 2015, nejsou k dispozici v CRT.

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```
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

#### <a name="parameters"></a>Parametry

*Port*<br/>
Číslo portu vstupně-výstupních operací.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí byte, word nebo double word přečtený z `port`. Není vrácena žádná chyba.

## <a name="remarks"></a>Poznámky

`_inp`, `_inpw`, A `_inpd` přečtou byte, word a double word, resp. ze zadaného vstupního portu. Vstupní hodnota může být jakékoli unsigned short integer v rozsahu 0 – 65 535.

Protože tyto funkce čtou přímo z I/O portu, nelze je použít v uživatelském kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|`_inp`|\<conio.h >|
|`_inpw`|\<conio.h >|
|`_inpd`|\<conio.h >|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [běhových knihoven C](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Viz také

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)