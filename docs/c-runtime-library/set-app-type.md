---
title: _set_app_type
ms.date: 4/2/2020
api_name:
- _set_app_type
- _o__set_app_type
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
ms.openlocfilehash: 9791cff55ccd55c32d124ab89cc43ab54c0f9c69
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360971"
---
# <a name="_set_app_type"></a>_set_app_type

Interní funkce použitá při spuštění sdělit CRT, zda je aplikace konzolové aplikace nebo GUI aplikace.

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
Hodnota, která označuje typ aplikace. Možné hodnoty jsou:

|Hodnota|Popis|
|----------------|-----------------|
|_crt_unknown_app|Neznámý typ aplikace.|
|_crt_console_app|Konzola (příkazový řádek) aplikace.|
|_crt_gui_app|GUI (Windows).|

## <a name="remarks"></a>Poznámky

Za normálních okolností není nutné volat tuto funkci. Je součástí spouštěcího kódu c runtime, `main` který se spustí před voláním ve vaší aplikaci.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_set_app_type|process.h|
