---
title: _set_app_type
ms.date: 11/04/2016
api_name:
- _set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 7e04d88d9e9981e35b7d4c80c11d27c868219f65
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957924"
---
# <a name="_set_app_type"></a>_set_app_type

Interní funkce použitá při spuštění k informování CRT, jestli je aplikace Konzolová aplikace nebo aplikace grafického uživatelského rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
typedef enum _crt_app_type
{
    _crt_unknown_app,
    _crt_console_app,
    _crt_gui_app
} _crt_app_type;

void __cdecl _set_app_type(
    _crt_app_type appType
    );
```

## <a name="parameters"></a>Parametry

*appType*<br/>
Hodnota, která určuje typ aplikace. Možné hodnoty jsou:

|Value|Popis|
|----------------|-----------------|
|_crt_unknown_app|Neznámý typ aplikace|
|_crt_console_app|Aplikace konzoly (příkazového řádku).|
|_crt_gui_app|Aplikace grafického uživatelského rozhraní (Windows).|

## <a name="remarks"></a>Poznámky

Obvykle nemusíte tuto funkci volat. Je součástí spouštěcího kódu modulu runtime jazyka C, který se `main` spustí před voláním ve vaší aplikaci.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_set_app_type|Process. h|
