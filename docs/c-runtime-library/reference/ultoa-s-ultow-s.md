---
title: "_ultoa_s –, _ultow_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ultow_s
- _ultoa_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ultow_s
- ultoa_s
- ultow_s
- _ultoa_s
dev_langs: C++
helpviewer_keywords:
- _ultoa_s function
- converting integers
- integers, converting
- _ultow_s function
- ultoa_s function
- converting numbers, to strings
- ultow_s function
ms.assetid: 606ce905-6752-46ac-a15a-bdc22920e1d4
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7968e8f7eb3d69ec40d0fddab75ec2abee348823
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ultoas-ultows"></a>_ultoa_s, _ultow_s
Dlouhé celé číslo bez znaménka převeďte na řetězec. Toto jsou verze [_ultoa –, _ultow –](../../c-runtime-library/reference/ultoa-ultow.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t _ultoa_s(  
    unsigned long value,  
    char *str,  
    size_t sizeOfstr,  
    int radix   
);  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t *str,  
    size_t sizeOfstr,  
    int radix   
);  
template <size_t size>  
errno_t _ultoa_s(  
    unsigned long value,  
    char (&str)[size],  
    int radix   
); // C++ only  
template <size_t size>  
errno_t _ultow_s(  
    unsigned long value,  
    wchar_t (&str)[size],  
    int radix   
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 Číslo, které má být převeden.  
  
 `str`  
 Řetězec výsledek.  
  
 `sizeOfstr`  
 Velikost `str` v bajtech pro `_ultoa_s` nebo slova pro `_ultow_s`.  
  
 `radix`  
 Základ `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Kód chyby nebo nula, pokud funkci byla úspěšná.  
  
## <a name="remarks"></a>Poznámky  
 `_ultoa_s` Funkce převede číslice z `value` na řetězec znaků ukončený hodnotou null a ukládá výsledků (až 33 bajtů) v `str`. `radix` Argument určuje základ `value`, která musí být v rozsahu 2 36. `_ultow_s`široká znaková verze `_ultoa_s`; druhý argument `_ultow_s` je široká znaková řetězce.  
  
 Pokud `str` je `NULL` ukazatele, nebo pokud `sizeOfstr` je menší než nebo rovna nule, je vyvolána obslužná rutina neplatný parametr, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno provádění pokračovat, tyto funkce vrátí hodnotu -1 a nastavte `errno` k `EINVAL` nebo, pokud `value` nebo `str` mimo rozsah dlouhých celých čísel, vrátí -1 a nastavte tyto funkce `errno` k `ERANGE`.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot_s`|`_ultoa_s`|`_ultoa_s`|`_ultow_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ultoa_s`|\<stdlib.h >|  
|`_ultow_s`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_ultoa –, _ultow –](../../c-runtime-library/reference/ultoa-ultow.md)   
 [_ltoa –, _ltow –](../../c-runtime-library/reference/ltoa-ltow.md)   
 [_ltoa_s –, _ltow_s –](../../c-runtime-library/reference/ltoa-s-ltow-s.md)   
 [_ltoa_s –, _ltow_s –](../../c-runtime-library/reference/ltoa-s-ltow-s.md)