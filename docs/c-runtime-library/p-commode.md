---
title: __p__commode
ms.date: 4/2/2020
api_name:
- __p__commode
- _o___p__commode
api_location:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: fa589c1972d27854e3f794d8283f49d9db5d053a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349308"
---
# <a name="__p__commode"></a>__p__commode

Odkazuje na `_commode` globální proměnnou, která určuje výchozí *režim potvrzení souboru* pro operace vstupně-videa souboru.

## <a name="syntax"></a>Syntaxe

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `_commode` globální proměnnou.

## <a name="remarks"></a>Poznámky

Funkce `__p__commode` je pouze pro interní použití a neměla by být volána z uživatelského kódu.

Režim potvrzení souboru určuje, kdy jsou důležitá data zapsána na disk. Další informace naleznete v tématu [fflush](../c-runtime-library/reference/fflush.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__commode|internal.h|
