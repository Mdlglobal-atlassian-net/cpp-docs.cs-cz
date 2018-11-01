---
title: __p__fmode
ms.date: 11/04/2016
apiname:
- __p__fmode
apilocation:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 59687cca87d283682c4b7231b5f8c1a55ff512db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579711"
---
# <a name="pfmode"></a>__p__fmode

Odkazuje `_fmode` globální proměnné, která určuje výchozí *režim překladu souboru* pro vstupně-výstupní operace.

## <a name="syntax"></a>Syntaxe

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel `_fmode` globální proměnné.

## <a name="remarks"></a>Poznámky

`__p__fmode` Funkce je jen pro interní použití a by neměla být volána z uživatelského kódu.

Určuje režim překladu souboru buď `binary` nebo `text` překlad pro [_Otevřít](../c-runtime-library/reference/open-wopen.md) a [_pipe –](../c-runtime-library/reference/pipe.md) vstupně-výstupních operací. Další informace najdete v tématu [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__fmode|stdlib.h|