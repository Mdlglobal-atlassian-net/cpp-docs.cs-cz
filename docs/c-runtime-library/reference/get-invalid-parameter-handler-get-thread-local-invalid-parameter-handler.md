---
title: _get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler
ms.date: 4/2/2020
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- _o__get_invalid_parameter_handler
- _o__get_thread_local_invalid_parameter_handler
api_location:
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 27e42c9f3f570b24df8fa2a26798b3dc3fa326b3
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82909895"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler, _get_thread_local_invalid_parameter_handler

Vrátí funkci, která je volána, když CRT detekuje neplatný argument.

## <a name="syntax"></a>Syntaxe

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuálně nastavenou funkci obslužné rutiny neplatného parametru nebo ukazatel s hodnotou null, pokud není nastaven.

## <a name="remarks"></a>Poznámky

Funkce **_get_invalid_parameter_handler** získá aktuálně nastavenou obslužnou rutinu globálního neplatného parametru. Vrátí ukazatel s hodnotou null, pokud nebyla nastavena žádná obslužná rutina globálního neplatného parametru. Podobně **_get_thread_local_invalid_parameter_handler** získá aktuální obslužnou rutinu neplatného místního vlákna vlákna, na kterou je volána, nebo ukazatel s hodnotou null, pokud nebyla nastavena žádná obslužná rutina. Informace o tom, jak nastavit globální obslužné rutiny parametrů globálních a místních vláken, naleznete v tématu [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Vrácený ukazatel na funkci obslužné rutiny neplatného parametru má následující typ:

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

Podrobnosti o obslužné rutině neplatného parametru naleznete v prototypu v [_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_get_invalid_parameter_handler** **_get_thread_local_invalid_parameter_handler**|C: \<Stdlib. h><br /><br /> C++: \<cstdlib> nebo \<Stdlib. h>|

Funkce **_get_invalid_parameter_handler** a **_get_thread_local_invalid_parameter_handler** jsou specifické pro společnost Microsoft. Informace o kompatibilitě najdete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také

[_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[Verze funkcí CRT se zdokonaleným zabezpečením](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
