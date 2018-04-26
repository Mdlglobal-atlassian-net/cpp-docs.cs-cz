---
title: _get_pgmptr – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _get_pgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_pgmptr
- _get_pgmptr
dev_langs:
- C++
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6af6203f8c6f40335a132f21929abf3cc4ce1808
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="getpgmptr"></a>_get_pgmptr

Získá aktuální hodnotu **_pgmptr –** – globální proměnná.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_pgmptr( 
   char **pValue 
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na řetězec tak, aby byla vyplněna s aktuální hodnota **_pgmptr –** proměnné.

## <a name="return-value"></a>Návratová hodnota

Vrátí nula v případě úspěšného; Kód chyby při selhání. Pokud *pValue* je **NULL**, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, tato funkce nastaví **errno** k **einval –** a vrátí **einval –**.

## <a name="remarks"></a>Poznámky

Volat pouze **_get_pgmptr –** Pokud má program úzké vstupní bod, třeba **main()** nebo **WinMain()**. **_Pgmptr –** – globální proměnná obsahuje úplnou cestu ke spustitelnému souboru spojených s procesem. Další informace najdete v tématu [_pgmptr –, _wpgmptr –](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_get_wpgmptr](get-wpgmptr.md)<br/>
