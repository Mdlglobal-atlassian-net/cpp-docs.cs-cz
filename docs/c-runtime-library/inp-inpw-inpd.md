---
title: _inp, _inpw, _inpd
ms.date: 11/04/2016
api_name:
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
- inpd
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
ms.openlocfilehash: 4668002fdf709e3e425ac379f136e228250896d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944981"
---
# <a name="_inp-_inpw-_inpd"></a>_inp, _inpw, _inpd

Vstupy, z portu, Byte (`_inp`), Word (`_inpw`) nebo Double Word (`_inpd`).

> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Počínaje verzí Visual Studio 2015 nejsou k dispozici v CRT.

> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime. Další informace najdete v tématu [funkce CRT nejsou v aplikacích Univerzální platforma Windows podporovány](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*přístavní*<br/>
Číslo portu I/O.

## <a name="return-value"></a>Návratová hodnota

Funkce vrátí bajt, slovo nebo Double Word čtený z `port`. Nevrátila se žádná chybová zpráva.

## <a name="remarks"></a>Poznámky

Funkce `_inp`, `_inpw` a`_inpd` čtou v zadaném vstupním portu bajt, slovo a dvojité slovo. Vstupní hodnota může být jakékoli krátké celé číslo bez znaménka v rozsahu 0-65 535.

Vzhledem k tomu, že tyto funkce jsou čteny přímo z portu I/O, nelze je použít v uživatelském kódu.

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

[I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)<br/>
[_outp, _outpw, _outpd](../c-runtime-library/outp-outpw-outpd.md)
