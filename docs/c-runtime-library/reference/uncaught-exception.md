---
title: __uncaught_exception
ms.date: 11/04/2016
apiname:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 19d1e18af27722d6f9da39ebaaf6c9415c281849
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268894"
---
# <a name="uncaughtexception"></a>__uncaught_exception

Označuje, zda jeden nebo více výjimek byla vyvolána výjimka, ale ještě nebyly zpracovány v odpovídajícím **catch** bloku [bloku try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) příkazu.

## <a name="syntax"></a>Syntaxe

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** od okamžiku dojde k výjimce **zkuste** bloku až do odpovídající **catch** blok je inicializována; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__uncaught_exception|eh.h|

## <a name="see-also"></a>Viz také:

[try, throw a catch – příkazy (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
