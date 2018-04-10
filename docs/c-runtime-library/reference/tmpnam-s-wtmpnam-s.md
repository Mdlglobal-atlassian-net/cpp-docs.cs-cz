---
title: tmpnam_s –, _wtmpnam_s – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- tmpnam_s
- _wtmpnam_s
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
dev_langs:
- C++
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 844da11b981b99d5fe69861c3198d0508857a1a5
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s, _wtmpnam_s
Generovat názvy, které můžete použít k vytvoření dočasné soubory. Toto jsou verze [tmpnam – a _wtmpnam –](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out] `str`  
 Ukazatel, který bude obsahovat vygenerovaný název.  
  
 [in] `sizeInChars`  
 Velikost vyrovnávací paměti ve znacích.  
  
## <a name="return-value"></a>Návratová hodnota  
 Obě tyto funkce na selhání vrátit 0, pokud bylo úspěšné nebo číslo chyby.  
  
### <a name="error-conditions"></a>Chybové stavy  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**Návratová hodnota**|**Obsah**  `str`|  
|`NULL`|všechny|`EINVAL`|nedojde ke změně|  
|Není `NULL` (odkazuje na platný paměti)|moc krátké.|`ERANGE`|nedojde ke změně|  
  
 Pokud `str` je `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění pokračovat, nastavte tyto funkce `errno` k `EINVAL` a vrátí `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí vrátí název souboru, který neexistuje. `tmpnam_s` Vrátí název jedinečný v aktuálním pracovním adresáři. Mějte na paměti než při pre čekajícího zpětným lomítkem a žádné informace o cestě, jako je například \fname21, název souboru to označuje, že název je platný pro aktuální pracovní adresář.  
  
 Pro `tmpnam_s`, můžete uložit tento název vygenerovaný soubor v `str`. Maximální délka řetězce vrácené `tmpnam_s` je `L_tmpnam_s`, definované v STDIO. H. Pokud `str` je `NULL`, pak `tmpnam_s` ponechá výsledek v statické vnitřní vyrovnávací paměť. Proto následných volání zrušte tuto hodnotu. Název generované `tmpnam_s` se skládá z názvu program vygeneroval soubor a po prvním volání `tmpnam_s`, příponu pořadová čísla v základní 32 (.1-.1vvvvvu, když `TMP_MAX_S` v STDIO. INT_MAX – je H).  
  
 `tmpnam_s` automaticky zpracovává argumenty řetězce vícebajtových znaků podle potřeby, rozpozná sekvencí vícebajtových znaků podle znakové stránky OEM získané z operačního systému. `_wtmpnam_s` široká charakterová verze `tmpnam_s`; argument a vrátí hodnotu `_wtmpnam_s` jsou široká charakterová řetězce. `_wtmpnam_s` a `tmpnam_s` vyjma toho, že se chovají stejně jako `_wtmpnam_s` nezpracovává řetězců vícebajtových znaků.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení lze odvodit délka vyrovnávací paměti automaticky, takže není nutné zadat argument velikost. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`tmpnam_s`|\<stdio.h>|  
|`_wtmpnam_s`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)