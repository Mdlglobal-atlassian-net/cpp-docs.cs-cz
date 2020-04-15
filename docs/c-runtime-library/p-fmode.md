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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: aecba640099719f90db8bbd5dbe386ea99aae45d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349251"
---
# <a name="__p__fmode"></a>__p__fmode

Odkazuje na `_fmode` globální proměnnou, která určuje výchozí *režim překladu souborů* pro operace vstupně-videa souborů.

## <a name="syntax"></a>Syntaxe

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `_fmode` globální proměnnou.

## <a name="remarks"></a>Poznámky

Funkce `__p__fmode` je pouze pro interní použití a neměla by být volána z uživatelského kódu.

Režim překladu souborů `binary` `text` určuje buď překlad [pro _open](../c-runtime-library/reference/open-wopen.md) a [_pipe](../c-runtime-library/reference/pipe.md) vstupně-va operace. Další informace naleznete [v tématu _fmode](../c-runtime-library/fmode.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
