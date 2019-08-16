---
title: memmove, wmemmove
ms.date: 11/04/2016
apiname:
- memmove
- wmemmove
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
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 27811f56f1956bcaaea4ec589f7e6c71afaca380
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69499620"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Přesune jednu vyrovnávací paměť do druhé. K dispozici jsou bezpečnější verze těchto funkcí; viz [memmove_s, wmemmove_s](memmove-s-wmemmove-s.md).

## <a name="syntax"></a>Syntaxe

```C
void *memmove(
   void *dest,
   const void *src,
   size_t count
);
wchar_t *wmemmove(
   wchar_t *dest,
   const wchar_t *src,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*propojovací*<br/>
Cílový objekt

*src*<br/>
Zdrojový objekt.

*výpočtu*<br/>
Počet bajtů (**memmove**) nebo znaků (**wmemmove**), které mají být zkopírovány.

## <a name="return-value"></a>Návratová hodnota

Hodnota *cíl*.

## <a name="remarks"></a>Poznámky

Kopíruje *počet* bajtů (**memmove**) nebo znaků (**wmemmove**) z *Src* na *cíl*. Pokud se některé oblasti zdrojové oblasti a cíle překrývají, obě funkce zajistí, že původní zdrojové bajty v překrývající se oblasti se před přepsáním zkopírují.

**Poznámka k zabezpečení** Ujistěte se, že cílová vyrovnávací paměť má stejnou velikost nebo je větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Funkce **memmove** a **wmemmove** budou zastaralé pouze v případě, že je konstanta **_CRT_SECURE_DEPRECATE_MEMORY** definována před příkazem include, aby byly funkce zastaralé, například v následujícím příkladu:

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <string.h>
```

or

```C
#define _CRT_SECURE_DEPRECATE_MEMORY
#include <wchar.h>
```

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**memmove**|\<String. h >|
|**wmemmove**|\<wchar.h>|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_memcpy.c
// Illustrate overlapping copy: memmove
// always handles it correctly; memcpy may handle
// it correctly.
//

#include <memory.h>
#include <string.h>
#include <stdio.h>

char str1[7] = "aabbcc";

int main( void )
{
   printf( "The string: %s\n", str1 );
   memcpy( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );

   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string

   printf( "The string: %s\n", str1 );
   memmove( str1 + 2, str1, 4 );
   printf( "New string: %s\n", str1 );
}
```

```Output
The string: aabbcc
New string: aaaabb
The string: aabbcc
New string: aaaabb
```

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[_memccpy](memccpy.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[strncpy, _strncpy_l, wcsncpy, _wcsncpy_l, _mbsncpy, _mbsncpy_l](strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)<br/>
