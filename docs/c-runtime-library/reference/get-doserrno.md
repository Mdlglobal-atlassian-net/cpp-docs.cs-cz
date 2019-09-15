---
title: _get_doserrno
ms.date: 11/04/2016
api_name:
- _get_doserrno
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2810ead8bdd7d6c77cb2b55f4f97371bfc9751e6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956042"
---
# <a name="_get_doserrno"></a>_get_doserrno

Získá hodnotu chyby vrácenou operačním systémem před tím, než se převede na hodnotu **errno** .

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na celé číslo, který má být vyplněn aktuální hodnotou **_doserrno** globálního makra.

## <a name="return-value"></a>Návratová hodnota

Pokud **_get_doserrno** uspěje, vrátí se nula; Pokud dojde k chybě, vrátí kód chyby. Pokud má PValue **hodnotu null**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce nastaví **errno** na **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

Globální makro **_doserrno** je během inicializace CRT nastaveno na nulu, než začne provádění procesu. Je nastavená na hodnotu chyby operačního systému vrácenou jakýmkoli voláním funkce na úrovni systému, které vrací chybu operačního systému a nikdy neresetuje na nulu během provádění. Při psaní kódu pro kontrolu hodnoty chyby vrácené funkcí vždy zrušte zaškrtnutí **_doserrno** pomocí [_set_doserrno](set-doserrno.md) před voláním funkce. Protože jiné volání funkce může přepsat **_doserrno**, podívejte se na hodnotu pomocí **_get_doserrno** hned po volání funkce.

Pro přenosné kódy chyb doporučujeme [_get_errno](get-errno.md) místo **_get_doserrno** .

Možné hodnoty **_doserrno** jsou definované v \<errno. h >.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h>, \<cerrno> (C++)|

**_get_doserrno** je rozšíření společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
