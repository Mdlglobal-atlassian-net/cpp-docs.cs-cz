---
title: _strdec, _wcsdec, _mbsdec, _mbsdec_l
ms.date: 4/2/2020
api_name:
- _wcsdec
- _strdec
- _mbsdec
- _mbsdec_l
- _o__mbsdec
- _o__mbsdec_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdec
- mbsdec_l
- strdec
- _mbsdec
- _mbsdec_l
- mbsdec
- wcsdec
- _wcsdec
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
ms.openlocfilehash: 57f8b092518c97e33b3972a569513fe678d168e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359803"
---
# <a name="_strdec-_wcsdec-_mbsdec-_mbsdec_l"></a>_strdec, _wcsdec, _mbsdec, _mbsdec_l

Přesune ukazatel řetězce o jeden znak zpět.

> [!IMPORTANT]
> **Mbsdec** a **mbsdec_l** nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime. Další informace naleznete v tématu [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

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

*Spustit*<br/>
Ukazatel na libovolný znak (nebo pro **_mbsdec** a **_mbsdec_l**, první bajt libovolného vícebajtového znaku) ve zdrojovém řetězci; *start* musí předcházet *proudu* ve zdrojovém řetězci.

*aktuální*<br/>
Ukazatel na libovolný znak (nebo pro **_mbsdec** a **_mbsdec_l**, první bajt libovolného vícebajtového znaku) ve zdrojovém řetězci; *proud* musí následovat *začátek* ve zdrojovém řetězci.

*Národní prostředí*<br/>
Národní prostředí použít.

## <a name="return-value"></a>Návratová hodnota

**_mbsdec**, **_mbsdec_l**, **_strdec**a **_wcsdec** každý vrátí ukazatel na znak, který bezprostředně předchází *proudu*; **_mbsdec** vrátí **hodnotu NULL,** pokud je hodnota *start* větší nebo rovna hodnotě *current*. **_tcsdec** mapuje na jednu z těchto funkcí a jeho vrácená hodnota závisí na mapování.

## <a name="remarks"></a>Poznámky

Funkce **_mbsdec** a **_mbsdec_l** vrátí ukazatel na první bajt vícebajtového znaku, který bezprostředně předchází *proudu* v řetězci, který obsahuje *start*.

Výstupní hodnota je ovlivněna nastavením nastavení **LC_CTYPE** kategorie národního prostředí; další informace naleznete [v _wsetlocale setlocale.](setlocale-wsetlocale.md)  **_mbsdec** rozpozná vícebajtové sekvence znaků podle národního prostředí, které je aktuálně používáno, zatímco **_mbsdec_l** je totožný s tím rozdílem, že místo toho používá parametr národního prostředí, který je předán. Další informace naleznete v [tématu Locale](../../c-runtime-library/locale.md).

Pokud *je* hodnota **NULL** *,* je vyvolána neplatná obslužná rutina parametru, jak je popsáno v části [Ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je spuštění povoleno pokračovat, vrátí tato funkce **funkce EINVAL** a nastaví **errno** na **EINVAL**.

> [!IMPORTANT]
> Tyto funkce mohou být náchylné k hrozbám přetečení vyrovnávací paměti. Přetečení vyrovnávací paměti lze použít pro systémové útoky, protože mohou způsobit neoprávněné zvýšení oprávnění. Další informace naleznete v [tématu Zabránění přetečení vyrovnávací paměti](/windows/win32/SecBP/avoiding-buffer-overruns).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Chcete-li to změnit, naleznete [v tématu Globální stav v CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu

|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsdec**|**_strdec**|**_mbsdec**|**_wcsdec**|

**_strdec** a **_wcsdec** jsou jednobajtové a širokoznakové verze **_mbsdec** a **_mbsdec_l**. **_strdec** a **_wcsdec** jsou k dispozici pouze pro toto mapování a jinak by neměly být používány.

Další informace naleznete [v tématu Použití mapování obecného textu](../../c-runtime-library/using-generic-text-mappings.md) a mapování [obecného textu](../../c-runtime-library/generic-text-mappings.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|Volitelná hlavička|
|-------------|---------------------|---------------------|
|**_mbsdec**|\<mbstring.h>|\<mbctype.h>|
|**_mbsdec_l**|\<mbstring.h>|\<mbctype.h>|
|**_strdec**|\<tchar.h>||
|**_wcsdec**|\<tchar.h>||

Další informace o kompatibilitě naleznete v [tématu Kompatibilita](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje použití **_tcsdec**.

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

## <a name="see-also"></a>Viz také

[Zacházení s řetězci](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_strinc, _wcsinc, _mbsinc, _mbsinc_l](strinc-wcsinc-mbsinc-mbsinc-l.md)<br/>
[_strnextc, _wcsnextc, _mbsnextc, _mbsnextc_l](strnextc-wcsnextc-mbsnextc-mbsnextc-l.md)<br/>
[_strninc, _wcsninc, _mbsninc, _mbsninc_l](strninc-wcsninc-mbsninc-mbsninc-l.md)<br/>
