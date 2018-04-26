---
title: fwide – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a055df312215b5ff424aff54cfee54e0568ab307
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="fwide"></a>fwide

Neimplementované.

## <a name="syntax"></a>Syntaxe

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>Parametry

*Datový proud*<br/>
Ukazatel na **souboru** struktury (Ignorovat).

*Režim*<br/>
Šířku nového datového proudu: kladné pro široká znaková záporné pro bajtů, nula ponechat beze změny. (Tato hodnota je ignorována.)

## <a name="return-value"></a>Návratová hodnota

Tato funkce je aktuálně právě vrací *režimu*.

## <a name="remarks"></a>Poznámky

Aktuální verze této funkce není v souladu se standardem.

## <a name="requirements"></a>Požadavky

|Funkce|Požadovaný hlavičkový soubor|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

Další informace najdete v tématu [kompatibility](../../c-runtime-library/compatibility.md).