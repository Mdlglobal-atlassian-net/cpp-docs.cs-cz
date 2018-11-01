---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
apiname:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
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
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 7d1a87f9ade0845994918d5a4d59dc56e190d2b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623974"
---
# <a name="getinvalidparameterhandler-getthreadlocalinvalidparameterhandler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Získá funkce, která je volána, když zjistí CRT neplatný argument.

## <a name="syntax"></a>Syntaxe

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně nastavené funkce obslužnou rutinu neplatného parametru, nebo nulový ukazatel, pokud žádná nastavení.

## <a name="remarks"></a>Poznámky

**_Get_invalid_parameter_handler** funkce získá v současné době nastavené globální neplatný parametr obslužné rutiny. Vrátí ukazatel s hodnotou null, pokud byl nastaven žádný globální neplatný parametr obslužné rutiny. Podobně platí **_get_thread_local_invalid_parameter_handler** získá aktuální obslužná rutina neplatného parametru místního vlákna vlákna je volán na nebo ukazatel s hodnotou null, pokud byla nastavena žádná obslužná rutina. Informace o tom, jak nastavit globální a místní neplatný parametr obslužné rutiny najdete v tématu [_set_invalid_parameter_handler – _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Ukazatel funkce vrácená neplatný parametr obslužné rutiny je následujícího typu:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Podrobnosti o obslužnou rutinu neplatného parametru, najdete v prototypu v [_set_invalid_parameter_handler – _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_invalid_parameter_handler**, **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h ><br /><br /> Jazyk C++: \<cstdlib – > nebo \<stdlib.h >|

**_Get_invalid_parameter_handler** a **_get_thread_local_invalid_parameter_handler** funkce jsou specifické pro Microsoft. Informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Verze funkcí CRT se zdokonaleným zabezpečením](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
