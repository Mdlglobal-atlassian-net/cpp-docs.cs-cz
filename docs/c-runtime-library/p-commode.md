---
title: __p__commode
ms.date: 11/04/2016
apiname:
- __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 3a565a179077635438c03539cefa83823603bb00
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289413"
---
# <a name="pcommode"></a>__p__commode

Odkazuje `_commode` globální proměnné, která určuje výchozí *potvrzení režim souboru* pro vstupně-výstupní operace.

## <a name="syntax"></a>Syntaxe

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel `_commode` globální proměnné.

## <a name="remarks"></a>Poznámky

`__p__commode` Funkce je jen pro interní použití a by neměla být volána z uživatelského kódu.

Určuje režim potvrzení souborů při zápisu důležitá data na disk. Další informace najdete v tématu [fflush –](../c-runtime-library/reference/fflush.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__p\__commode|internal.h|