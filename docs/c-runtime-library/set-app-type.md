---
title: _set_app_type | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- _set_app_type
apilocation:
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_app_type
- corecrt_startup/_set_app_type
dev_langs:
- C++
ms.assetid: 1e7fe786-b587-4116-8c05-f7d762350100
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2ad7e22bf6ba366a33dd44ce49c1a384f88b87
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46041256"
---
# <a name="setapptype"></a>_set_app_type

Vnitřní funkce, která používá při spuštění říct CRT, jestli je aplikace konzolové aplikace nebo aplikace s grafickým uživatelským rozhraním.

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
|_crt_unknown_app|Neznámý typ aplikace.|
|_crt_console_app|Aplikace konzoly (příkazového řádku).|
|_crt_gui_app|Aplikace grafického uživatelského rozhraní (Windows).|

## <a name="remarks"></a>Poznámky

Za normálních okolností není potřeba voláním této funkce. Je součástí C runtime spouštěcí kód, který se spustí před `main` nazývá ve vaší aplikaci.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_set_app_type|Process.h|

