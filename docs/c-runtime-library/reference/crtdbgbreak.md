---
title: _CrtDbgBreak
ms.date: 11/04/2016
api_name:
- _CrtDbgBreak
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 9471b1a93abd9777c3a53c54c2517e59896d8160
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942585"
---
# <a name="_crtdbgbreak"></a>_CrtDbgBreak

Nastaví bod přerušení na konkrétní řádek kódu. (Používáno pouze v režimu ladění.)

## <a name="syntax"></a>Syntaxe

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>Návratová hodnota

Neexistuje žádná návratová hodnota.

## <a name="remarks"></a>Poznámky

Funkce **_CrtDbgBreak** nastaví zarážku ladění na konkrétní řádek kódu, kde je funkce umístěna. Tato funkce se používá jenom v režimu ladění a je závislá na **_DEBUG** , která je dřív definovaná.

Další informace o používání dalších funkcí běhu s podporou zavěšení a psaní vlastních funkcí zavěšení definovaných klientem najdete v tématu [Zápis vlastních funkcí ladicího programu](/visualstudio/debugger/debug-hook-function-writing).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>Knihovny

Ladit verze pouze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Viz také:

[Rutiny ladění](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
