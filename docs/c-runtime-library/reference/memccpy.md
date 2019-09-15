---
title: _memccpy
ms.date: 11/04/2016
api_name:
- _memccpy
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _memccpy
helpviewer_keywords:
- _memccpy function
- memccpy function
ms.assetid: 9a2337df-6e85-4eba-b247-dd0532f45ddb
ms.openlocfilehash: 097cefb504ffcdbfbe6bf131d5e8b1837d11a47a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951969"
---
# <a name="_memccpy"></a>_memccpy

Kopíruje znaky z vyrovnávací paměti.

## <a name="syntax"></a>Syntaxe

```C
void *_memccpy(
   void *dest,
   const void *src,
   int c,
   size_t count
);
```

### <a name="parameters"></a>Parametry

*propojovací*<br/>
Ukazatel na cíl.

*src*<br/>
Ukazatel na zdroj.

*c*<br/>
Poslední znak ke zkopírování.

*výpočtu*<br/>
Počet znaků.

## <a name="return-value"></a>Návratová hodnota

Pokud je znak *c* zkopírován, vrátí **_memccpy** ukazatel na znak v příkazu *cíl* , který následuje bezprostředně za znakem. Pokud není *c* zkopírován, vrátí **hodnotu null**.

## <a name="remarks"></a>Poznámky

Funkce **_memccpy** kopíruje 0 nebo více znaků *Src* na *cíl*, zastaví se, když byl znak *c* zkopírován nebo když byly zkopírovány znaky *Count* , podle toho, co nastane dřív.

**Poznámka k zabezpečení** Ujistěte se, že cílová vyrovnávací paměť má stejnou velikost nebo je větší než zdrojová vyrovnávací paměť. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_memccpy**|\<Memory. h > nebo \<String. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Knihovny

Všechny verze [knihoven run-time jazyka C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Příklad

```C
// crt_memccpy.c

#include <memory.h>
#include <stdio.h>
#include <string.h>

char string1[60] = "The quick brown dog jumps over the lazy fox";

int main( void )
{
   char buffer[61];
   char *pdest;

   printf( "Function: _memccpy 60 characters or to character 's'\n" );
   printf( "Source: %s\n", string1 );
   pdest = _memccpy( buffer, string1, 's', 60 );
   *pdest = '\0';
   printf( "Result: %s\n", buffer );
   printf( "Length: %d characters\n", strlen( buffer ) );
}
```

### <a name="output"></a>Výstup

```Output
Function: _memccpy 60 characters or to character 's'
Source: The quick brown dog jumps over the lazy fox
Result: The quick brown dog jumps
Length: 25 characters
```

## <a name="see-also"></a>Viz také:

[Zacházení s vyrovnávací pamětí](../../c-runtime-library/buffer-manipulation.md)<br/>
[memchr, wmemchr](memchr-wmemchr.md)<br/>
[memcmp, wmemcmp](memcmp-wmemcmp.md)<br/>
[memcpy, wmemcpy](memcpy-wmemcpy.md)<br/>
[memset, wmemset](memset-wmemset.md)<br/>
