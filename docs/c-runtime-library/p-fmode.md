---
title: __p__fmode
ms.date: 11/04/2016
api_name:
- __p__fmode
api_location:
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __p__fmode
helpviewer_keywords:
- __p__fmode
ms.assetid: 1daa1394-81eb-43aa-a71b-4cc6acf3207b
ms.openlocfilehash: 2364a22d52c5bc418e4499a4a639c8e06559063a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171447"
---
# <a name="__p__fmode"></a>__p__fmode

Odkazuje na `_fmode` globální proměnná, která určuje výchozí *režim překladu souborů* pro vstupně-výstupní operace se soubory.

## <a name="syntax"></a>Syntaxe

```cpp
int* __p__fmode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na `_fmode` globální proměnnou.

## <a name="remarks"></a>Poznámky

Funkce `__p__fmode` je určena pouze pro interní použití a neměla by být volána z uživatelského kódu.

Režim překladu souborů Určuje buď `binary` nebo `text` překlad pro [_open](../c-runtime-library/reference/open-wopen.md) a [_Pipe](../c-runtime-library/reference/pipe.md) vstupně-výstupních operací. Další informace najdete v tématu [_fmode](../c-runtime-library/fmode.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__fmode|stdlib.h|
