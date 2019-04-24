---
title: _getmbcp
ms.date: 11/04/2016
apiname:
- _getmbcp
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
- _getmbcp
- getmbcp
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
ms.openlocfilehash: 4cea84fc771a1d847814d002294391256efae57b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157640"
---
# <a name="getmbcp"></a>_getmbcp

Načte aktuální znakové stránce.

## <a name="syntax"></a>Syntaxe

```C
int _getmbcp( void );
```

## <a name="return-value"></a>Návratová hodnota

Vrátí aktuální vícebajtové znakové stránky. Vrácená hodnota 0 znamená, že jednobajtová znaková stránka je používán.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_getmbcp**|\<mbctype.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_setmbcp](setmbcp.md)<br/>
