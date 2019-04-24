---
title: fwide
ms.date: 11/04/2016
apiname:
- fwide
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
apitype: DLLExport
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: d992ebc527744beeb4ef14175e3f10646a77a064
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287613"
---
# <a name="fwide"></a>fwide

Neimplementovaná.

## <a name="syntax"></a>Syntaxe

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parametry

*stream*<br/>
Ukazatel na **souboru** struktury (ignorováno).

*Režim*<br/>
Novou šířku datového proudu: kladné pro široký znak, záporné pro byte, nula ponechat beze změny. (Tato hodnota se ignoruje.)

## <a name="return-value"></a>Návratová hodnota

Tato funkce aktuálně jenom vrací *režimu*.

## <a name="remarks"></a>Poznámky

Aktuální verze této funkce není v souladu se standardem.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).