---
title: memmove_s, wmemmove_s
ms.date: 11/04/2016
apiname:
- wmemmove_s
- memmove_s
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wmemmove_s
- memmove_s
helpviewer_keywords:
- wmemmove_s function
- memmove_s function
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
ms.openlocfilehash: 7b60174c3a06e60301a3e9123434220227f4f426
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561184"
---
# <a name="memmoves-wmemmoves"></a>memmove_s, wmemmove_s

Jeden vyrovnávací paměti přesune do jiné. Jde o verzích [memmove wmemmove –](memmove-wmemmove.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*cíl*<br/>
Cílový objekt.

*numberOfElements*<br/>
Velikost cílové vyrovnávací paměti.

*src*<br/>
Zdrojový objekt.

*Počet*<br/>
Počet bajtů (**memmove_s –**) nebo znaky (**wmemmove_s –**) ke kopírování.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; při selhání kód chyby

### <a name="error-conditions"></a>Chybové podmínky

|*cíl*|*numberOfElements*|*src*|Návratová hodnota|Obsah *dest*|
|------------|------------------------|-----------|------------------|------------------------|
|**HODNOTU NULL**|Všechny|Všechny|**EINVAL**|Nezměněno|
|Všechny|Všechny|**HODNOTU NULL**|**EINVAL**|Nezměněno|
|Všechny|< *Počet*|Všechny|**ERANGE**|Nezměněno|

## <a name="remarks"></a>Poznámky

Kopie *počet* bajtů ze znaků *src* k *dest*. Pokud se některé oblasti oblasti zdroj a cíl překrývají, **memmove_s –** zajistí, že se zkopírují původní zdroj bajtů překrývající se oblasti před přepsáním.

Pokud *dest* nebo, pokud *src* je ukazatel s hodnotou null, nebo pokud cílový řetězec je moc malé, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md) . Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** a nastavte **errno** k **EINVAL**.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memmove_s –**|\<String.h >|
|**wmemmove_s**|\<wchar.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy_s, wcscpy_s, _mbscpy_s](strcpy-s-wcscpy-s-mbscpy-s.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
