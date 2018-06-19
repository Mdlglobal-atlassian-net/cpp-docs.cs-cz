---
title: _strrev –, _wcsrev –, _mbsrev _mbsrev_l – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcsrev
- _mbsrev
- _strrev
- _mbsrev_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strrev
- _ftcsrev
- _tcsrev
- mbsrev
- mbsrev_l
- _wcsrev_fstrrev
- _mbsrev
dev_langs:
- C++
helpviewer_keywords:
- _mbsrev_l function
- characters [C++], switching
- _mbsrev function
- strrev function
- _ftcsrev function
- strings [C++], reversing
- wcsrev function
- _strrev function
- mbsrev_l function
- reversing characters in strings
- ftcsrev function
- characters [C++], reversing order
- _wcsrev function
- mbsrev function
- tcsrev function
- _tcsrev function
ms.assetid: 87863e89-4fa0-421c-af48-25d8516fe72f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 52b99b08fc7761f5fb2d15761bf7726ac0faf64d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415423"
---
# <a name="strrev-wcsrev-mbsrev-mbsrevl"></a>_strrev, _wcsrev, _mbsrev, _mbsrev_l

Obrátí znaky řetězce.

> [!IMPORTANT]
> **_mbsrev** a **_mbsrev_l –** nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
char *_strrev(
   char *str
);
wchar_t *_wcsrev(
   wchar_t *str
);
unsigned char *_mbsrev(
   unsigned char *str
);
unsigned char *_mbsrev_l(
   unsigned char *str,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*str –*<br/>
Řetězce ukončené hodnotou Null a obrátit.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

Vrací ukazatel na změněna řetězec. Žádnou návratovou hodnotu je vyhrazena indikující chybu.

## <a name="remarks"></a>Poznámky

**_Strrev –** funkce obrátí pořadí znaků v *str*. Ukončovací znak hodnoty null zůstává na místě. **_wcsrev –** a **_mbsrev** jsou široká charakterová a vícebajtových znaků verze **_strrev –**. Argumenty a vrací hodnotu **_wcsrev –** jsou široká charakterová řetězce; u **_mbsrev** jsou řetězců vícebajtových znaků. Pro **_mbsrev**, pořadí bajtů v každé vícebajtových znaků v *str* se nezmění. Tyto tři funkce chovají stejně jako jinak.

**_mbsrev** ověří jeho parametry. Pokud má jedna *řetězec1* nebo *řetězec2* je ukazatel s hodnotou null, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění **_mbsrev** vrátí **NULL** a nastaví **errno** k **einval –**. **_strrev –** a **_wcsrev –** neověřují jejich parametrů.

Výstupní hodnota je ovlivňován nastavením **LC_CTYPE –** kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít **_l** příponu použít aktuální národní prostředí a ty, které mají **_l** příponu, použijte parametr národního prostředí to je Předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).

> [!IMPORTANT]
> Tato funkce může být zranitelný vůči hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti můžete použít pro útoky systému, protože může dojít k tomu bude vyplacena neoprávněně zvýšení úrovně oprávnění. Další informace najdete v tématu [zabraňující způsobí přetečení vyrovnávací paměti](http://msdn.microsoft.com/library/windows/desktop/ms717795).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsrev –**|**_strrev**|**_mbsrev**|**_wcsrev**|
|**není k dispozici**|**není k dispozici**|**_mbsrev_l**|**není k dispozici**|

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|**_strrev**|\<String.h >|
|**_wcsrev**|\<String.h > nebo \<wchar.h >|
|**_mbsrev**, **_mbsrev_l –**|\<Mbstring.h >|

Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

```C
// crt_strrev.c
// This program checks a string to see
// whether it is a palindrome: that is, whether
// it reads the same forward and backward.
//

#include <string.h>
#include <stdio.h>

int main( void )
{
   char* string = "Able was I ere I saw Elba";
   int result;

   // Reverse string and compare (ignore case):
   result = _stricmp( string, _strrev( _strdup( string ) ) );
   if( result == 0 )
      printf( "The string \"%s\" is a palindrome\n", string );
   else
      printf( "The string \"%s\" is not a palindrome\n", string );
}
```

```Output
The string "Able was I ere I saw Elba" is a palindrome
```

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Národní prostředí](../../c-runtime-library/locale.md)<br/>
[Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcpy, wcscpy, _mbscpy](strcpy-wcscpy-mbscpy.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
