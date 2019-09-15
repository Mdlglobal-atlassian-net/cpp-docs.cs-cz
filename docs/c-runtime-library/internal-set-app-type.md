---
title: __set_app_type
ms.date: 11/04/2016
api_name:
- __set_app_type
- _set_app_type
api_location:
- msvcr90.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcrt.dll
- msvcr120.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __set_app_type
helpviewer_keywords:
- __set_app_type
ms.assetid: f0ac0f4d-70e6-4e96-9e43-eb9d1515490c
ms.openlocfilehash: 4d72eecd454e6c01e88c6869c96b628902690383
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940229"
---
# <a name="__set_app_type"></a>__set_app_type

Nastaví typ aktuální aplikace.

## <a name="syntax"></a>Syntaxe

```cpp
void __set_app_type (
   int at
   )
```

#### <a name="parameters"></a>Parametry

*at*<br/>
Hodnota, která určuje typ aplikace. Možné hodnoty jsou:

|Value|Popis|
|-----------|-----------------|
|_UNKNOWN_APP|Neznámý typ aplikace|
|_CONSOLE_APP|Aplikace konzoly (příkazového řádku).|
|_GUI_APP|Aplikace grafického uživatelského rozhraní (Windows).|

## <a name="remarks"></a>Poznámky

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__set_app_type|internal.h|