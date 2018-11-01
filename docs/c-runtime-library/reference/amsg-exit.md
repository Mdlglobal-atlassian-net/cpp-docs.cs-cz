---
title: _amsg_exit
ms.date: 11/04/2016
apiname:
- _amsg_exit
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _amsg_exit
helpviewer_keywords:
- _amsg_exit
ms.assetid: 146d4faf-d763-43a4-b264-12711196456b
ms.openlocfilehash: 87cd08a6c60a1e29b8a8e15edbfdd69d338d875d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534023"
---
# <a name="amsgexit"></a>_amsg_exit

Vydá chybovou zprávu zadaného modulu runtime a následně skončí aplikace s kódem chyby 255.

## <a name="syntax"></a>Syntaxe

```cpp
void _amsg_exit ( int rterrnum );
```

### <a name="parameters"></a>Parametry

*rterrnum*<br/>
Identifikační číslo chybovou zprávu modulu runtime definované v systému.

## <a name="remarks"></a>Poznámky

Tato funkce generuje runtime chybová zpráva na **stderr** pro konzolové aplikace a zobrazí zprávy ve zprávě pole pro aplikace Windows. V režimu ladění můžete vyvolat ladicí program před ukončením.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|_amsg_exit|internal.h|