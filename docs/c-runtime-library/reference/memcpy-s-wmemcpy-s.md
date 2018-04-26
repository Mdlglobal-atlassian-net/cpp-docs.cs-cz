---
title: memcpy_s –, wmemcpy_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
apitype: DLLExport
f1_keywords:
- wmemcpy_s
- memcpy_s
dev_langs:
- C++
helpviewer_keywords:
- memcpy_s function
- wmemcpy_s function
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5442f70e246dd8e82a6f7b3e1e78810c6d197f41
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2018
---
# <a name="memcpys-wmemcpys"></a>memcpy_s, wmemcpy_s

Počet bajtů kopie mezi vyrovnávací paměti. Toto jsou verze [memcpy wmemcpy –](memcpy-wmemcpy.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).

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

*Cíle*<br/>
Vyrovnávací paměť nového.

*destSize*<br/>
Cílová vyrovnávací paměť v bajtech pro memcpy_s – a široké znaky (wchar_t) pro wmemcpy_s – velikost.

*src*<br/>
Zkopírovat z vyrovnávací paměti.

*Počet*<br/>
Počet znaků pro kopírování.

## <a name="return-value"></a>Návratová hodnota

Nula v případě úspěšného; Kód chyby při selhání.

### <a name="error-conditions"></a>Chybové stavy

|*Cíle*|*destSize*|*src*|*Počet*|Návratová hodnota|Obsah *cíle*|
|------------|----------------|-----------|---|------------------|------------------------|
|všechny|všechny|všechny|0|0|nedojde ke změně|
|**HODNOTU NULL**|všechny|všechny|nulová|**EINVAL –**|nedojde ke změně|
|všechny|všechny|**HODNOTU NULL**|nulová|**EINVAL –**|*cíle* je dojde k vynulování|
|všechny|< *Počet*|všechny|nulová|**ERANGE –**|*cíle* je dojde k vynulování|

## <a name="remarks"></a>Poznámky

**memcpy_s –** kopie *počet* bajtů z *src* k *cíle*; **wmemcpy_s –** kopie *počet* široké znaky (dva bajty). Pokud zdrojové a cílové překrývají, chování **memcpy_s –** není definován. Použití **memmove_s –** pro zpracování překrývající se oblasti.

Tyto funkce ověřit jejich parametrů. Pokud *počet* je nulová a *cíle* nebo *src* je ukazatel s hodnotou null, nebo *destSize* je menší než *počet*, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **einval –** nebo **erange –** a nastavte **errno** na návratovou hodnotu.

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memcpy_s**|\<Memory.h > nebo \<string.h >|
|**wmemcpy_s**|\<wchar.h>|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

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

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memmove, wmemmove](memmove-wmemmove.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
