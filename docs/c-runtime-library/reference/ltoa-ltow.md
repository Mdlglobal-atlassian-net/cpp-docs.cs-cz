---
title: "_ltoa –, _ltow – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ltoa
- _ltow
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
- ltow
- _ltot
- _ltoa
- _ltow
dev_langs: C++
helpviewer_keywords:
- converting integers
- _ltoa function
- _ltow function
- ltow function
- ltoa function
- long integer conversion to string
- converting numbers, to strings
ms.assetid: 14036104-2c25-4759-87c0-918ed8521e47
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 135c082e4d972b18af057bf22a718ac9c4170718
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ltoa-ltow"></a>_ltoa, _ltow
Převede dlouhých celých čísel na řetězec. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_ltoa_s –, _ltow_s –](../../c-runtime-library/reference/ltoa-s-ltow-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_ltoa(  
   long value,  
   char *str,  
   int radix   
);  
wchar_t *_ltow(  
   long value,  
   wchar_t *str,  
   int radix   
);  
template <size_t size>  
char *_ltoa(  
   long value,  
   char (&str)[size],  
   int radix   
); // C++ only  
template <size_t size>  
wchar_t *_ltow(  
   long value,  
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
 `_ltoa` Funkce převede číslice z `value` na řetězec znaků ukončený hodnotou null a ukládá výsledků (až 33 bajtů) v `str`. `radix` Argument určuje základ `value`, která musí být v rozsahu 2 36. Pokud `radix` rovná 10 a `value` je záporná, je první znak uložené řetězce znaménka minus (-). `_ltow`široká charakterová verze `_ltoa`; druhý argument a vrátí hodnotu `_ltow` jsou široká charakterová řetězce. Každá z těchto funkcí je specifické pro společnost Microsoft.  
  
> [!IMPORTANT]
>  Chcete-li zabránit přetečení vyrovnávací paměti, ověřte, zda `str` vyrovnávací paměť je dostatečně velký pro uložení převedený číslic plus koncové znak hodnoty null a znak znaménka.  
  
 V jazyce C++ tyto funkce mají přetížení šablony. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_ltot`|`_ltoa`|`_ltoa`|`_ltow`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ltoa`|\<stdlib.h >|  
|`_ltow`|\<stdlib.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad pro [_itoa –](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_itoa –, _i64toa –, _ui64toa –, _itow –, _i64tow –, _ui64tow –](../../c-runtime-library/reference/itoa-i64toa-ui64toa-itow-i64tow-ui64tow.md)   
 [_ultoa –, _ultow –](../../c-runtime-library/reference/ultoa-ultow.md)