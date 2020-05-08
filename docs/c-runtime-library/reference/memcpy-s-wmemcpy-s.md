---
title: memcpy_s, wmemcpy_s
ms.date: 4/2/2020
api_name:
- memcpy_s
- wmemcpy_s
- _o_memcpy_s
- _o_wmemcpy_s
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
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 7b3df3542974f99009285c8df652cff1fd4fa173
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915408"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Kopíruje bajty mezi vyrovnávacími paměťmi. Jedná se o verze [memcpy, wmemcpy](memcpy-wmemcpy.md) s vylepšeními zabezpečení, jak [je popsáno v části funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Syntaxe

```C
errno_t memcpy_s(
   void *dest,
   size_t destSize,
   const void *src,
   size_t count
);
errno_t wmemcpy_s(
   wchar_t *dest,
   size_t destSize,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*propojovací*<br/>
Nová vyrovnávací paměť.

*destSize*<br/>
Velikost cílové vyrovnávací paměti v bajtech pro memcpy_s a velké znaky (wchar_t) pro wmemcpy_s.

*src*<br/>
Vyrovnávací paměť, ze které se má kopírovat.

*výpočtu*<br/>
Počet znaků, které mají být zkopírovány.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; chybový kód při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*propojovací*|*destSize*|*src*|*výpočtu*|Návratová hodnota|Obsah cíle *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|jakýmikoli|jakýmikoli|jakýmikoli|0|0|Neupraveno|
|**PLATNOST**|jakýmikoli|jakýmikoli|bez nuly|**EINVAL**|Neupraveno|
|jakýmikoli|jakýmikoli|**PLATNOST**|bez nuly|**EINVAL**|*cíl* je nula|
|jakýmikoli|< *výpočtu*|jakýmikoli|bez nuly|**ERANGE**|*cíl* je nula|

## <a name="remarks"></a>Poznámky

**memcpy_s** kopíruje *počet* bajtů ze *Src* na *cíl*; **wmemcpy_s** kopíruje *počet* znaků, které jsou v rozsahu (dva bajty). Pokud se zdrojový a cílový překrývají, chování **memcpy_s** není definováno. Použijte **memmove_s** k obsluze překrývajících se oblastí.

Tyto funkce ověřují své parametry. Pokud je *počet* nenulový a *cíl* nebo *Src* je ukazatel s hodnotou null, nebo *destSize* je menší než *Count*, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** nebo **ERANGE** a nastaví **errno** na vrácenou hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy_s**|\<Memory. h> nebo \<String. h>|
|**wmemcpy_s**|\<WCHAR. h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_memcpy_s.c
// Copy memory in a more secure way.

#include <memory.h>
#include <stdio.h>

int main()
{
   int a1[10], a2[100], i;
   errno_t err;

   // Populate a2 with squares of integers
   for (i = 0; i < 100; i++)
   {
      a2[i] = i*i;
   }

   // Tell memcpy_s to copy 10 ints (40 bytes), giving
   // the size of the a1 array (also 40 bytes).
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );
   if (err)
   {
      printf("Error executing memcpy_s.\n");
   }
   else
   {
     for (i = 0; i < 10; i++)
       printf("%d ", a1[i]);
   }
   printf("\n");
}
```

```Output
0 1 4 9 16 25 36 49 64 81
```

## <a name="see-also"></a>Viz také

[Manipulace s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
