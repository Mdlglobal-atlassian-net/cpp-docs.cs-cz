---
title: _get_fmode – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_fmode
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_fmode
- _get_fmode
dev_langs:
- C++
helpviewer_keywords:
- _get_fmode function
- file translation [C++], default mode
- get_fmode function
ms.assetid: 22ea70e2-b9b5-422d-b514-64f4beaea45c
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3a3845de8feb36b995fec8d450bfc5a9656d429c
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getfmode"></a>_get_fmode

Získá výchozí režim překladu souboru pro soubor vstupně-výstupních operací.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_fmode( 
   int * pmode 
);
```

### <a name="parameters"></a>Parametry

*pmode*<br/>
Ukazatel na celé číslo, aby byla vyplněna s aktuální výchozí režim: **_o_text –** nebo **_o_binary –**.

## <a name="return-value"></a>Návratová hodnota

Vrátí nula v případě úspěšného; Kód chyby při selhání. Pokud *pmode* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **errno** je nastaven na **einval –** a funkce vrátí hodnotu **einval –**.

## <a name="remarks"></a>Poznámky

Získá hodnotu funkce [_fmode –](../../c-runtime-library/fmode.md) – globální proměnná. Tato proměnná Určuje výchozí režim překladu souboru pro obě nízké úrovně a stream vstupně-výstupní operace, jako například **_Otevřít**, **_pipe –**, **fopen –**, a [ freopen –](freopen-wfreopen.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|
|-------------|---------------------|---------------------|
|**_get_fmode**|\<stdlib.h>|\<fcntl.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Podívejte se na příklad v [_set_fmode –](set-fmode.md).

## <a name="see-also"></a>Viz také

[_fmode](../../c-runtime-library/fmode.md)<br/>
[_set_fmode](set-fmode.md)<br/>
[_setmode](setmode.md)<br/>
[I/O soubor textového a binárního režimu](../../c-runtime-library/text-and-binary-mode-file-i-o.md)<br/>
