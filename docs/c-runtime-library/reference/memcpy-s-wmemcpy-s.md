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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: dc5e49115b65b6883e55df13d0610231a87c1c55
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333341"
---
# <a name="memcpy_s-wmemcpy_s"></a>memcpy_s, wmemcpy_s

Zkopíruje bajty mezi vyrovnávacími paměťmi. Jedná se o verze [memcpy, wmemcpy](memcpy-wmemcpy.md) s vylepšeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Dest*<br/>
Nová vyrovnávací paměť.

*destSize*<br/>
Velikost cílové vyrovnávací paměti v bajtech pro memcpy_s a široké znaky (wchar_t) pro wmemcpy_s.

*src*<br/>
Vyrovnávací paměť, ze které se má kopírovat.

*Počet*<br/>
Počet znaků ke kopírování.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*Dest*|*destSize*|*src*|*Počet*|Návratová hodnota|Obsah *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|jakékoli|jakékoli|jakékoli|0|0|Nezměněno|
|**Null**|jakékoli|jakékoli|nenulová|**EINVAL**|Nezměněno|
|jakékoli|jakékoli|**Null**|nenulová|**EINVAL**|*dest* je vynulován|
|jakékoli|< *Počet*|jakékoli|nenulová|**ERANGE**|*dest* je vynulován|

## <a name="remarks"></a>Poznámky

**memcpy_s** kopie *počítají* bajty od *src* do *dest*; **wmemcpy_s** kopie *počítají* široké znaky (dva bajty). Pokud se zdroj a cíl překrývají, chování **memcpy_s** není definováno. Pomocí **memmove_s** můžete zpracovávat překrývající se oblasti.

Tyto funkce ověřují jejich parametry. Pokud *count* je nenulová a *dest* nebo *src* je nulový ukazatel nebo *destSize* je menší než *count*, tyto funkce vyvolat neplatný parametr obslužné rutiny, jak je popsáno v [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí **EINVAL** nebo **ERANGE** a nastavit **errno** na vrácenou hodnotu.

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy_s**|\<memory.h> \<nebo string.h>|
|**wmemcpy_s**|\<wchar.h>|

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

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
