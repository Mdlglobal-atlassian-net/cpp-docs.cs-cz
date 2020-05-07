---
title: __p__fmode
ms.date: 4/2/2020
api_name:
- __p__fmode
- _o___p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: dfd9962c49b03dbb30223d1d7403b791ed6dbec9
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919878"
---
# <a name="__p__fmode"></a>__p__fmode

Odkazuje na `_fmode` globální proměnnou, která určuje výchozí *režim překladu souborů* pro vstupně-výstupní operace souborů.

## <a name="syntax"></a>Syntaxe

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `_fmode` globální proměnnou.

## <a name="remarks"></a>Poznámky

`__p__fmode` Funkce je určena pouze pro interní použití a neměla by být volána z uživatelského kódu.

Režim překladu souborů Určuje buď `binary` nebo `text` překlad pro [_open](../c-runtime-library/reference/open-wopen.md) a vstupně-výstupní operace [_pipe](../c-runtime-library/reference/pipe.md) . Další informace najdete v tématu [_fmode](../c-runtime-library/fmode.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__fmode|Stdlib. h|
