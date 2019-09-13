---
title: __uncaught_exception
ms.date: 11/04/2016
api_name:
- __uncaught_exception
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
- __uncaught_exception
helpviewer_keywords:
- __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
ms.openlocfilehash: 0130776ec2511aefd42d1700f950d97738e9fb14
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945952"
---
# <a name="__uncaught_exception"></a>__uncaught_exception

Určuje, zda byla vyvolána jedna nebo více výjimek, ale ještě nebyly zpracovány odpovídajícím blokem **catch** příkazu [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md) .

## <a name="syntax"></a>Syntaxe

```cpp
bool __uncaught_exception(
   );
```

## <a name="return-value"></a>Návratová hodnota

**true** v době, kdy je výjimka vyvolána v bloku **Try** , dokud se neinicializuje vyhovující blok **catch** ; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__uncaught_exception|Eh. h|

## <a name="see-also"></a>Viz také:

[try, throw a catch – příkazy (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)<br/>
