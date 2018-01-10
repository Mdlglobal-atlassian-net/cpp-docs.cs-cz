---
title: "_tempnam –, _wtempnam –, tmpnam –, _wtmpnam – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs: C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9708c23fc76095a591a2eceafcb875ce173383ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam, _wtempnam, tmpnam, _wtmpnam
Generovat názvy, které můžete použít k vytvoření dočasné soubory. Bezpečnější verze některé z těchto funkcí jsou k dispozici. v tématu [tmpnam_s –, _wtmpnam_s –](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `prefix`  
 Řetězec, který bude pre čekajícího na názvy vrácený `_tempnam`.  
  
 `dir`  
 Cesty použité v názvu souboru, pokud neexistuje žádná proměnná prostředí TMP, nebo pokud TMP není platný adresář.  
  
 `str`  
 Ukazatele, který bude obsahovat vygenerovaný název a musí být stejný název vráceným funkcí. Toto je pohodlný způsob, jak uložit vygenerovaný název.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrací ukazatel na název vygenerovaný nebo `NULL` Pokud dojde k selhání. Selhání může dojít, pokud se pokusíte více než `TMP_MAX` (viz STDIO. H) volání s `tmpnam` nebo pokud používáte `_tempnam` a je neplatný název adresáře zadané v proměnné prostředí TMP a v `dir` parametr.  
  
> [!NOTE]
>  Následující ukazatele vrácený `tmpnam` a `_wtmpnam` přejděte na interní statické vyrovnávací paměti. [volné](../../c-runtime-library/reference/free.md) by neměl být volán se zrušit přidělení tyto ukazatele. `free`musí být volána pro ukazatele přidělené `_tempnam` a `_wtempnam`.  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí vrátí název souboru, který neexistuje. `tmpnam`Vrátí název jedinečný v aktuální pracovní adresář a `_tempnam` umožňuje generovat jedinečný název v adresáři, než jaký je aktuální. Mějte na paměti než při pre čekajícího zpětným lomítkem a žádné informace o cestě, jako je například \fname21, název souboru to označuje, že název je platný pro aktuální pracovní adresář.  
  
 Pro `tmpnam`, můžete uložit tento název vygenerovaný soubor v `str`. Pokud `str` je `NULL`, pak `tmpnam` ponechá výsledek v statické vnitřní vyrovnávací paměť. Proto následných volání zrušte tuto hodnotu. Název generované `tmpnam` se skládá z názvu program vygeneroval soubor a po prvním volání `tmpnam`, příponu pořadová čísla v základní 32 (.1-.vvu, když `TMP_MAX` v STDIO. H je 32 767.)  
  
 `_tempnam`vygeneruje se jedinečný název souboru pro adresář vybrali podle následujících pravidel:  
  
-   Pokud proměnná prostředí TMP je definovaný a nastavena na platný název adresáře, vygeneruje se pro adresář zadaný TMP jedinečných názvů souborů.  
  
-   Pokud proměnná prostředí TMP není definovaná nebo pokud je nastavena na název adresáře, který neexistuje, `_tempnam` použije `dir` parametr jako cestu, pro který vygeneruje jedinečné názvy.  
  
-   Pokud není definována proměnná prostředí TMP nebo pokud je nastavena na název adresáře, který ještě neexistuje a pokud `dir` je buď `NULL` nebo nastavte na název adresáře, který neexistuje, `_tempnam` použije aktuální pracovní adresář pro gen míra jedinečné názvy. V současné době pokud obě TMP a `dir` zadáte názvy adresáře, které neexistují, `_tempnam` volání funkce se nezdaří.  
  
 Vrácený název `_tempnam` bude zřetězení `prefix` a pořadové číslo, které bude kombinací vytvořit jedinečný název souboru pro zadaný adresář. `_tempnam`vygeneruje názvy souborů, které mají žádné rozšíření. `_tempnam`používá [malloc](../../c-runtime-library/reference/malloc.md) k přidělení místa pro název souboru; tento program je zodpovědná za uvolnění tento prostor, když už ho nepotřebují.  
  
 `_tempnam`a `tmpnam` automaticky popisovač vícebajtových znaků argumenty řetězce podle potřeby, rozpozná sekvencí vícebajtových znaků podle znakové stránky OEM získány z operačního systému. `_wtempnam`široká charakterová verze `_tempnam`; argumentů a návratová hodnota `_wtempnam` jsou široká charakterová řetězce. `_wtempnam`a `_tempnam` vyjma toho, že se chovají stejně jako `_wtempnam` nezpracovává řetězců vícebajtových znaků. `_wtmpnam`široká charakterová verze `tmpnam`; argument a vrátí hodnotu `_wtmpnam` jsou široká charakterová řetězce. `_wtmpnam`a `tmpnam` vyjma toho, že se chovají stejně jako `_wtmpnam` nezpracovává řetězců vícebajtových znaků.  
  
 Pokud `_DEBUG` a `_CRTDBG_MAP_ALLOC` jsou definovány `_tempnam` a `_wtempnam` jsou nahrazovány volání [_tempnam_dbg – a _wtempnam_dbg –](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_tempnam`|\<stdio.h >|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h > nebo \<wchar.h >|  
|`tmpnam`|\<stdio.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
```Output  
\s1gk. is safe to use as a temporary file.  
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [_getmbcp –](../../c-runtime-library/reference/getmbcp.md)   
 [malloc –](../../c-runtime-library/reference/malloc.md)   
 [_setmbcp –](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile –](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)