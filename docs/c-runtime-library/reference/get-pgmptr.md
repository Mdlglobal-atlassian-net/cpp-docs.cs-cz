---
title: _get_pgmptr
ms.date: 11/04/2016
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
helpviewer_keywords:
- get_pgmptr function
- _get_pgmptr function
- pgmptr global variable
- _pgmptr global variable
ms.assetid: 29f16a9f-a685-4721-add3-7fad4f67eece
ms.openlocfilehash: 2d3959a69d85fca38e4d099d3365553f88fd015f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62287499"
---
# <a name="getpgmptr"></a>_get_pgmptr

Získá aktuální hodnotu **_pgmptr –** globální proměnné.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_pgmptr(
   char **pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na řetězec tankujeme aktuální hodnota **_pgmptr –** proměnné.

## <a name="return-value"></a>Návratová hodnota

Vrátí nulu v případě úspěchu; Kód chyby při selhání. Pokud *pValue* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Volat pouze **_get_pgmptr –** Pokud program neobsahuje úzký vstupního bodu, jako jsou **main()** nebo **WinMain()**. **_Pgmptr –** globální proměnná obsahuje úplnou cestu ke spustitelnému souboru spojených s procesem. Další informace najdete v tématu [_pgmptr – _wpgmptr –](../../c-runtime-library/pgmptr-wpgmptr.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_pgmptr**|\<stdlib.h>|

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_get_wpgmptr](get-wpgmptr.md)<br/>
