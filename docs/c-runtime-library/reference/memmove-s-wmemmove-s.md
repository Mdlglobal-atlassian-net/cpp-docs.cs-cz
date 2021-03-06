---
title: memmove_s, wmemmove_s
ms.date: 4/2/2020
api_name:
- wmemmove_s
- memmove_s
- _o_wmemmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 04f920543c4f6a3d433e6426a96d617a3608a270
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914086"
---
# <a name="memmove_s-wmemmove_s"></a>memmove_s, wmemmove_s

Přesune jednu vyrovnávací paměť do druhé. Jedná se o verze [memmove, wmemmove](memmove-wmemmove.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t memmove_s(
   void *dest,
   size_t numberOfElements,
   const void *src,
   size_t count
);
errno_t wmemmove_s(
   wchar_t *dest,
   size_t numberOfElements,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*propojovací*<br/>
Cílový objekt

*numberOfElements*<br/>
Velikost cílové vyrovnávací paměti.

*src*<br/>
Zdrojový objekt.

*výpočtu*<br/>
Počet bajtů (**memmove_s**) nebo znaků (**wmemmove_s**), které mají být zkopírovány.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání

### <a name="error-conditions"></a>Chybové stavy

|*propojovací*|*numberOfElements*|*src*|Návratová hodnota|Obsah cíle *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**PLATNOST**|jakýmikoli|jakýmikoli|**EINVAL**|Neupraveno|
|jakýmikoli|jakýmikoli|**PLATNOST**|**EINVAL**|Neupraveno|
|jakýmikoli|< *výpočtu*|jakýmikoli|**ERANGE**|Neupraveno|

## <a name="remarks"></a>Poznámky

Zkopíruje *počet* bajtů znaků ze *Src* na *cíl*. Pokud se některé oblasti zdrojové oblasti a cíle překrývají, **memmove_s** zajistí, že původní zdrojové bajty v překrývající se oblasti budou před přepsáním zkopírovány.

Pokud je parametr Destination nebo pokud *Src* je ukazatel s hodnotou null *, nebo pokud* je cílový řetězec příliš malý, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastaví **errno** na **EINVAL**.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memmove_s**|\<String. h>|
|**wmemmove_s**|\<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_memmove_s.c
//
// The program demonstrates the
// memmove_s function which works as expected
// for moving overlapping regions.

#include <stdio.h>
#include <string.h>

int main()
{
   char str[] = "0123456789";

   printf("Before: %s\n", str);

   // Move six bytes from the start of the string
   // to a new position shifted by one byte. To protect against
   // buffer overrun, the secure version of memmove requires the
   // the length of the destination string to be specified.

   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);

   printf_s(" After: %s\n", str);
}
```

### <a name="output"></a>Výstup

```Output
Before: 0123456789
After: 0012345789
```

## <a name="see-also"></a>Viz také

[Manipulace s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
