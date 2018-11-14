---
title: _get_doserrno
ms.date: 11/04/2016
apiname:
- _get_doserrno
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
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 700f710e6d94f48b03697325bb720dbc539fe04e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331019"
---
# <a name="getdoserrno"></a>_get_doserrno

Získá chybovou hodnotu vrátí operačního systému, než je převeden do **errno** hodnotu.

## <a name="syntax"></a>Syntaxe

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parametry

*pValue*<br/>
Ukazatel na celé číslo tankujeme aktuální hodnota **_doserrno** globálního makra.

## <a name="return-value"></a>Návratová hodnota

Pokud **_get_doserrno –** úspěšná, vrátí 0; Pokud selže, vrátí kód chyby. Pokud *pValue* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud smí provádění pokračovat, tato funkce nastaví **errno** k **EINVAL** a vrátí **EINVAL**.

## <a name="remarks"></a>Poznámky

**_Doserrno** globálního makra je nastaven na hodnotu nula během inicializace CRT, proces spuštění začne. Je nastavena na hodnotu Chyba operačního systému vrácené voláním funkce na úrovni systému, která vrací chybu operačního systému a je nikdy resetuje na nulu během provádění. Při psaní kódu ke kontrole chyb hodnoty vrácené funkcí, vždy jasné **_doserrno** pomocí [_set_doserrno –](set-doserrno.md) před voláním funkce. Vzhledem k tomu může dojít k přepsání jiného volání funkce **_doserrno**, zkontrolujte hodnotu s použitím **_get_doserrno –** ihned po volání funkce.

Doporučujeme [_get_errno –](get-errno.md) místo **_get_doserrno –** pro přenosné chybové kódy.

Možné hodnoty **_doserrno** jsou definovány v \<errno.h >.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h >, \<cstdlib – > (C++)|\<errno.h >, \<cerrno – > (C++)|

**_get_doserrno –** je rozšířením společnosti Microsoft. Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Viz také:

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
