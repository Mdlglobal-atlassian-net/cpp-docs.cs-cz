---
title: memcpy_s, wmemcpy_s
ms.date: 11/04/2016
apiname:
- memcpy_s
- wmemcpy_s
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
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- wmemcpy_s
- memcpy_s
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
ms.openlocfilehash: 802d75307096e649df15b1864b99699fba92a3a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62285328"
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s

Kopie bajtů mezi vyrovnávací paměti. Jde o verzích [memcpy wmemcpy –](memcpy-wmemcpy.md) s rozšířeními zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*dest*<br/>
Vyrovnávací paměť nového.

*destSize*<br/>
Velikost cílové vyrovnávací paměti v bajtech pro memcpy_s – a široké znaky (wchar_t) pro wmemcpy_s –.

*src*<br/>
Zkopírovat z vyrovnávací paměti.

*Počet*<br/>
Počet znaků, které mají kopírovat.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěchu; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové podmínky

|*dest*|*destSize*|*src*|*Počet*|Návratová hodnota|Obsah *dest*|
|------------|----------------|-----------|---|------------------|------------------------|
|Všechny|Všechny|Všechny|0|0|Nezměněno|
|**NULL**|Všechny|Všechny|nulová|**EINVAL**|Nezměněno|
|Všechny|Všechny|**NULL**|nulová|**EINVAL**|*DEST* je vynulován|
|Všechny|< *Počet*|Všechny|nulová|**ERANGE**|*DEST* je vynulován|

## <a name="remarks"></a>Poznámky

**memcpy_s –** kopie *počet* bajtů z *src* k *dest*; **wmemcpy_s –** kopie *počet* široké znaky (dva bajty). Pokud zdroj a cíl překrývají, chování **memcpy_s –** není definován. Použití **memmove_s –** zpracování překrývající se oblasti.

Tyto funkce ověřují své parametry. Pokud *počet* je nenulová a *dest* nebo *src* je ukazatel s hodnotou null, nebo *destSize* je menší než *počet*, tyto funkce vyvolají obslužnou rutinu neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EINVAL** nebo **ERANGE** a nastavte **errno** návratovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy_s**|\<Memory.h > nebo \<string.h >|
|**wmemcpy_s**|\<wchar.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
