---
title: _get_pgmptr – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0488e2a7b8cd907872e835abb63e62f29f259455
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397776"
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
