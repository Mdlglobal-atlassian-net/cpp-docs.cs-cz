---
title: "_ultoa –, _ultow – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _ultoa
- _ultow
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
- ultot
- ultow
- _ultoa
- _ultow
- _ultot
dev_langs:
- C++
helpviewer_keywords:
- ultot function
- converting integers
- _ultot function
- ultow function
- integers, converting
- _ultow function
- _ultoa function
- converting numbers, to strings
ms.assetid: 7a472dc4-5652-4513-93c3-3358522c23be
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 94073b947848199bdc093f959ddceadcb1835f16
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="ultoa-ultow"></a>_ultoa, _ultow
Dlouhé celé číslo bez znaménka převeďte na řetězec. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_ultoa_s –, _ultow_s –](../../c-runtime-library/reference/ultoa-s-ultow-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_ultoa(  
   unsigned long value,  
   char *str,  
   int radix   
);  
wchar_t *_ultow(  
   unsigned long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ultoa(  
   unsigned long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ultow(  
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
  
 `radix`  
 Základ `value`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí ukazatel na `str`. Neexistuje žádný návratový chyby.  
  
## <a name="remarks"></a>Poznámky  
 `_ultoa` Funkce převede `value` na řetězec znaků ukončený hodnotou null a ukládá výsledků (až 33 bajtů) v `str`. Neprobíhá žádná kontrola přetečení. `radix` Určuje základ `value`; `radix` musí být v rozsahu 2 36. `_ultow` široká charakterová verze `_ultoa`.  
  
> [!IMPORTANT]
>  Chcete-li zabránit přetečení vyrovnávací paměti, ověřte, zda `str` vyrovnávací paměť je dostatečně velký pro uložení převedený číslic plus koncové znak hodnoty null.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ultot`|`_ultoa`|`_ultoa`|`_ultow`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ultoa`|\<stdlib.h>|  
|`_ultow`|\<stdlib.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_itoa –](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_itoa, _i64toa, _ui64toa, _itow, _i64tow, _ui64tow](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)