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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 057a0146aed87a50fc2e8c444b97a8b7b51eada1
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919501"
---
# <a name="__p__commode"></a>__p__commode

Odkazuje na `_commode` globální proměnnou, která určuje výchozí *režim potvrzení souborů* pro vstupně-výstupní operace se soubory.

## <a name="syntax"></a>Syntaxe

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `_commode` globální proměnnou.

## <a name="remarks"></a>Poznámky

`__p__commode` Funkce je určena pouze pro interní použití a neměla by být volána z uživatelského kódu.

Režim potvrzení souboru určuje, kdy se na disk zapisují kritická data. Další informace najdete v tématu [fflush](../c-runtime-library/reference/fflush.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__commode|interní. h|
