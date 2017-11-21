---
title: "_ltoa_s –, _ltow_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ltoa_s
- _ltow_s
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
apitype: DLLExport
f1_keywords:
- _ltow_s
- _ltoa_s
- ltoa_s
- ltow_s
dev_langs: C++
helpviewer_keywords:
- converting integers
- _ltoa_s function
- ltow_s function
- long integer conversion to string
- converting numbers, to strings
- ltoa_s function
- _ltow_s function
ms.assetid: d7dc61ea-1ccd-412d-b262-555a58647386
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a9a6bc0bc74463ad38cc43a0adb514d9eb722783
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltoas-ltows"></a>_ltoa_s, _ltow_s
Převede dlouhých celých čísel na řetězec. Toto jsou verze [_ltoa –, _ltow –](../../c-runtime-library/reference/ltoa-ltow.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _ltoa_s(  
    long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ltow_s(  
    long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ltoa_s(  
    long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ltow_s(  
    long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Číslo, které má být převeden.  
  
 `str`  
 Vyrovnávací paměť pro výsledný řetězec.  
  
 `sizeOfstr`  
 Velikost `str` v bajtech pro `_ltoa_s` nebo slova pro `_ltow_s`.  
  
 `radix`  
 Základ `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kód chyby nebo nula, pokud funkci byla úspěšná.  
  
## <a name="remarks"></a>Poznámky  
 `_ltoa_s` Funkce převede číslice z `value` na řetězec znaků ukončený hodnotou null a ukládá výsledků (až 33 bajtů) v `str`. `radix` Argument určuje základ `value`, která musí být v rozsahu 2 36. Pokud `radix` rovná 10 a `value` je záporná, je první znak uložené řetězce znaménka minus (-). `_ltow_s`široká znaková verze `_ltoa_s`; druhý argument `_ltow_s` je široká znaková řetězce.  
  
 Pokud `str` je `NULL` ukazatel nebo `sizeOfstr` je menší než nebo rovna nule, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL` nebo, pokud `value` nebo `str` mimo rozsah dlouhých celých čísel, vrátí -1 tyto funkce a nastavte `errno` k `ERANGE`.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot_s`|`_ltoa_s`|`_ltoa_s`|`_ltow_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ltoa_s`|\<stdlib.h >|  
|`_ltow_s`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_itoa –, _i64toa –, _ui64toa –, _itow –, _i64tow –, _ui64tow –](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa –, _ultow –](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ultoa_s –, _ultow_s –](../../c-runtime-library/reference/ultoa-s-ultow-s.md)