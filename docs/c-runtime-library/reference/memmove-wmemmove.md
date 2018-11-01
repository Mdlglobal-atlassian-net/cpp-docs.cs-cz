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
apitype: DLLExport
f1_keywords:
- memmove
- wmemmove
helpviewer_keywords:
- wmemmove function
- memmove function
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
ms.openlocfilehash: 8801e43ee10f99b5c18a6b2340449da7a433aaf1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50599858"
---
# <a name="memmove-wmemmove"></a>memmove, wmemmove

Jeden vyrovnávací paměti přesune do jiné. Bezpečnější verze těchto funkcí jsou k dispozici. Zobrazit [memmove_s – wmemmove_s –](memmove-s-wmemmove-s.md).

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

*cíl*<br/>
Cílový objekt.

*src*<br/>
Zdrojový objekt.

*Počet*<br/>
Počet bajtů (**memmove**) nebo znaky (**wmemmove –**) ke kopírování.

## <a name="return-value"></a>Návratová hodnota

Hodnota *dest*.

## <a name="remarks"></a>Poznámky

Kopie *počet* bajtů (**memmove**) nebo znaky (**wmemmove –**) z *src* k *dest*. Pokud se některé oblasti oblasti zdroj a cíl překrývají, obě funkce Ujistěte se, že se zkopírují původní zdroj bajtů překrývající se oblasti před přepsáním.

**Poznámka k zabezpečení** Ujistěte se, že cílová vyrovnávací paměť je stejný velké nebo větší než zdrojové vyrovnávací paměti. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

**Memmove** a **wmemmove –** funkce se nepoužívají pouze pokud konstanty **_CRT_SECURE_DEPRECATE_MEMORY** je definovaná před příkazem zahrnutí v pořadí Funkce zastaralé, například v následujícím příkladu:

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
|**memmove**|\<String.h >|
|**wmemmove –**|\<wchar.h>|

Další informace o kompatibilitě, naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

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
