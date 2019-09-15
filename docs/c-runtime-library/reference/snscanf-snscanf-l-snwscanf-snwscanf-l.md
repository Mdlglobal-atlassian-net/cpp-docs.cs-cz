---
title: _snscanf, _snscanf_l, _snwscanf, _snwscanf_l
ms.date: 11/04/2016
api_name:
- _snwscanf
- _snscanf_l
- _snscanf
- _snwscanf_l
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _snscanf
- _snscanf_l
- _snwscanf
- snscanf_l
- snscanf
- _sntscanf_l
- _sntscanf
- _snwscanf_l
- sntscanf_l
- sntscanf
- snwscanf
- snwscanf_l
helpviewer_keywords:
- snscanf_l function
- snwscanf function
- _sntscanf_l function
- sntscanf function
- _snwscanf_l function
- _sntscanf function
- _snscanf_l function
- sntscanf_l function
- strings [C++], reading data from
- snscanf function
- snwscanf_l function
- _snwscanf function
- reading data, strings
- strings [C++], reading
- _snscanf function
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
ms.openlocfilehash: f259eede1b2927b4676467c3450504f7ff7c19de
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947932"
---
# <a name="_snscanf-_snscanf_l-_snwscanf-_snwscanf_l"></a>_snscanf, _snscanf_l, _snwscanf, _snwscanf_l

Přečte formátovaná data o zadané délce z řetězce. K dispozici jsou bezpečnější verze těchto funkcí; viz [_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l](snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md).

## <a name="syntax"></a>Syntaxe

```C
int __cdecl _snscanf(
   const char * input,
   size_t length,
   const char * format,
   ...
);
int __cdecl _snscanf_l(
   const char * input,
   size_t length,
   const char * format,
   locale_t locale,
   ...
);
int __cdecl _snwscanf(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   ...
);
int __cdecl _snwscanf_l(
   const wchar_t * input,
   size_t length,
   const wchar_t * format,
   locale_t locale,
   ...
);
```

### <a name="parameters"></a>Parametry

*vstup*<br/>
Vstupní řetězec, který se má prošetřit

*length*<br/>
Počet znaků, které mají být zkontrolovány ve *vstupu*.

*format*<br/>
Jeden nebo více specifikátorů formátu.

*...*<br/>
Volitelné proměnné, které budou použity k uložení hodnot extrahovaných ze vstupního řetězce specifikátory formátu ve *formátu*.

*jazyka*<br/>
Národní prostředí, které se má použít

## <a name="return-value"></a>Návratová hodnota

Obě tyto funkce vrátí počet úspěšně převedených a přiřazených polí. Vrácená hodnota nezahrnuje pole, která byla načtena, ale nebyla přiřazena. Návratová hodnota 0 značí, že nebyla přiřazena žádná pole. Návratová hodnota je znak **EOF** pro chybu, nebo pokud je dosaženo konce řetězce před prvním převodem. Další informace najdete v tématu [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Pokud je *vstup* nebo *Formát* ukazatel s **hodnotou null** , nebo pokud je *Délka* menší nebo rovna nule, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v tématu [ověřování parametru](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, vrátí tyto funkce **EOF** a nastaví **errno** na **EINVAL**.

Informace o těchto a dalších chybových kódech naleznete v tématu [_doserrno, errno, _sys_errlist a _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Poznámky

Tato funkce se podobá **sscanf** s tím rozdílem, že poskytuje možnost zadat pevný počet znaků, které se mají prozkoumávat ze vstupního řetězce. Další informace najdete v tématu [sscanf](sscanf-sscanf-l-swscanf-swscanf-l.md).

Verze těchto funkcí s příponou **_l** jsou stejné s tím rozdílem, že používají předaný parametr národního prostředí namísto aktuálního národního prostředí vlákna.

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_sntscanf**|**_snscanf**|**_snscanf**|**_snwscanf**|
|**_sntscanf_l**|**_snscanf_l**|**_snscanf_l**|**_snwscanf_l**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_snscanf**, **_snscanf_l**|\<stdio.h>|
|**_snwscanf**, **_snwscanf_l**|\<stdio. h > nebo \<WCHAR. h >|

Další informace o kompatibilitě naleznete v tématu [Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_snscanf.c
// compile with: /W3

#include <stdio.h>
int main( )
{
   char  str1[] = "15 12 14...";
   wchar_t  str2[] = L"15 12 14...";
   char  s1[3];
   wchar_t  s2[3];
   int   i;
   float fp;

   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996
   // Note: _snscanf is deprecated; consider using _snscanf_s instead
   printf("_snscanf converted %d fields: ", i);
   printf("%s and %f\n", s1, fp);

   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead
   wprintf(L"_snwscanf converted %d fields: ", i);
   wprintf(L"%s and %f\n", s2, fp);
}
```

```Output
_snscanf converted 2 fields: 15 and 12.000000
_snwscanf converted 2 fields: 15 and 12.000000
```

## <a name="see-also"></a>Viz také:

[scanf – specifikace šířky](../../c-runtime-library/scanf-width-specification.md)<br/>
