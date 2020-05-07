---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 2b78b7205b1e5dda7ac7062747c6dd1065ed1c94
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919920"
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

*Typ aplikace*<br/>
Hodnota, která určuje typ aplikace. Možné hodnoty jsou:

|Hodnota|Popis|
|----------------|-----------------|
|_crt_unknown_app|Neznámý typ aplikace|
|_crt_console_app|Aplikace konzoly (příkazového řádku).|
|_crt_gui_app|Aplikace grafického uživatelského rozhraní (Windows).|

## <a name="remarks"></a>Poznámky

Obvykle nemusíte tuto funkci volat. Je součástí spouštěcího kódu modulu runtime jazyka C, který se `main` spustí před voláním ve vaší aplikaci.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_set_app_type|Process. h|
