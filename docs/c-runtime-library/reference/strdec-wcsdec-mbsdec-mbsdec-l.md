---
title: _strdec – _wcsdec –, _mbsdec _mbsdec_l – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
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
apitype: DLLExport
f1_keywords:
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
dev_langs:
- C++
helpviewer_keywords:
- mbsdec_l function
- mbsdec function
- tcsdec function
- _tcsdec function
- _strdec function
- _wcsdec function
- _mbsdec_l function
- strdec function
- wcsdec function
- _mbsdec function
ms.assetid: ae37c223-800f-48a9-ae8e-38c8d20af2dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a700d6e7befb71b1161ec27beb7a839f93e003e
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43211471"
---
# <a name="strdec-wcsdec-mbsdec-mbsdecl"></a>_strdec, _wcsdec, _mbsdec, _mbsdec_l

Přejde zpět o jeden znak řetězec ukazatele.

> [!IMPORTANT]
> **mbsdec –** a **mbsdec_l –** nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime. Další informace najdete v tématu [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntaxe

```C
unsigned char *_strdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned wchar_t *_wcsdec(
   const unsigned wchar_t *start,
   const unsigned wchar_t *current
);
unsigned char *_mbsdec(
   const unsigned char *start,
   const unsigned char *current
);
unsigned char *_mbsdec_l(
   const unsigned char *start,
   const unsigned char *current,
   _locale_t locale
);
```

### <a name="parameters"></a>Parametry

*Spuštění*<br/>
Ukazatel na libovolný znak (nebo pro **_mbsdec** a **_mbsdec_l –**, první bajt libovolného vícebajtového znaku) ve zdrojovém řetězci; *start* musí předcházet *aktuální* ve zdrojovém řetězci.

*aktuální*<br/>
Ukazatel na libovolný znak (nebo pro **_mbsdec** a **_mbsdec_l –**, první bajt libovolného vícebajtového znaku) ve zdrojovém řetězci; *aktuální* musí následovat *start* ve zdrojovém řetězci.

*Národní prostředí*<br/>
Národní prostředí.

## <a name="return-value"></a>Návratová hodnota

**_mbsdec**, **_mbsdec_l –**, **_strdec –**, a **_wcsdec –** vrátí ukazatel na znak, který bezprostředně předchází *aktuální*; **_mbsdec** vrátí **NULL** Pokud hodnota *start* je větší než nebo rovna hodnotě *aktuální*. **_tcsdec –** mapuje na jednu z těchto funkcí a vrácená hodnota závisí na mapování.

## <a name="remarks"></a>Poznámky

**_Mbsdec** a **_mbsdec_l –** funkce vrátí ukazatel na první bajt vícebajtového znaku, která bezprostředně předchází *aktuální* v řetězci, který obsahuje *start*.

Výstupní hodnota je ovlivněna nastavením **LC_CTYPE** nastavením kategorie národního prostředí; viz [setlocale _wsetlocale](setlocale-wsetlocale.md) Další informace.  **_mbsdec** rozpozná vícebajtové znakové sekvence podle národního prostředí, která je aktuálně používán, zatímco **_mbsdec_l –** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí, které je předáno. Další informace najdete v tématu [národní prostředí](../../c-runtime-library/locale.md).

Pokud *start* nebo *aktuální* je **NULL**, je vyvolána obslužná rutina neplatného parametru, jak je popsáno v [Parameter Validation](../../c-runtime-library/parameter-validation.md). Pokud provádění může pokračovat, tato funkce vrací **EINVAL** a nastaví **errno** k **EINVAL**.

> [!IMPORTANT]
> Tyto funkce by mohly být vystaveny ohrožení přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení úrovně oprávnění. Další informace najdete v tématu [předcházení přetečení vyrovnávací paměti](/windows/desktop/SecBP/avoiding-buffer-overruns).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsdec –**|**_strdec**|**_mbsdec**|**_wcsdec**|

**_strdec –** a **_wcsdec –** jsou jedním jednobajtového znaku a širokoznaká verze **_mbsdec** a **_mbsdec_l –**. **_strdec –** a **_wcsdec –** jsou k dispozici pouze pro toto mapování a nesmí být použity jinak.

Další informace najdete v tématu [použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a [mapování obecného textu](../../c-runtime-library/generic-text-mappings.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelné záhlaví|
|-------------|---------------------|---------------------|
|**_mbsdec**|\<Mbstring.h >|\<Mbctype.h >|
|**_mbsdec_l**|\<Mbstring.h >|\<Mbctype.h >|
|**_strdec**|\<tchar.h>||
|**_wcsdec**|\<tchar.h>||

Další informace o kompatibilitě naleznete v tématu [kompatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití **_tcsdec –**.

```cpp
// crt_tcsdec.cpp
// Compile by using: cl /EHsc crt_tcsdec.cpp
#include <iostream>
#include <tchar.h>
using namespace std;

int main()
{
   const TCHAR *str = _T("12345");
   cout << "str: " << str << endl;

   const TCHAR *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   TCHAR *answer;
   answer = _tcsdec( str, str2 );
   cout << "answer: " << answer << endl;

   return (0);
}
```

Následující příklad ukazuje použití **_mbsdec**.

```cpp
// crt_mbsdec.cpp
// Compile by using: cl /EHsc crt_mbsdec.c
#include <iostream>
#include <mbstring.h>
using namespace std;

int main()
{
   char *str = "12345";
   cout << "str: " << str << endl;

   char *str2;
   str2 = str + 2;
   cout << "str2: " << str2 << endl;

   unsigned char *answer;
   answer = _mbsdec( reinterpret_cast<unsigned char *>( str ), reinterpret_cast<unsigned char *>( str2 ));

   cout << "answer: " << answer << endl;

   return (0);
}
```

## <a name="see-also"></a>Viz také:

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
