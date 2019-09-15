---
title: _abnormal_termination
ms.date: 11/04/2016
api_name:
- _abnormal_termination
api_location:
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _abnormal_termination
helpviewer_keywords:
- _abnormal_termination
ms.assetid: 952970a4-9586-4c3d-807a-db729448c91c
ms.openlocfilehash: b66cf0df998b4e33a9f3425fdf0f260d163f423b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944714"
---
# <a name="_abnormal_termination"></a>_abnormal_termination

Určuje, zda `__finally` je zapsán blok [příkazu try-finally](../cpp/try-finally-statement.md) , zatímco systém provádí interní seznam obslužných rutin ukončení.

## <a name="syntax"></a>Syntaxe

```cpp
int   _abnormal_termination(
   );
```

## <a name="return-value"></a>Návratová hodnota

**true** , pokud systém *odvíjí* od zásobníku; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Toto je interní funkce, která slouží ke správě výjimek unwind, a není určena pro volání z uživatelského kódu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_abnormal_termination|EXCPT. h|

## <a name="see-also"></a>Viz také:

[try-finally – příkaz](../cpp/try-finally-statement.md)
