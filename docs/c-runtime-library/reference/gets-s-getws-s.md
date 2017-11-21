---
title: "gets_s –, _getws_s – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getws_s
- gets_s
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
- _getws_s
- gets_s
dev_langs: C++
helpviewer_keywords:
- getws_s function
- _getws_s function
- lines, getting
- streams, getting lines
- buffers, avoiding overruns
- buffer overruns
- buffers, buffer overruns
- gets_s function
- standard input, reading from
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea0c9053ef052359a0dc827299ade1ef2bbcb20f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="getss-getwss"></a>gets_s, _getws_s
Získá řádek z `stdin` datového proudu. Tyto verze nástroje [získá _getws –](../../c-runtime-library/gets-getws.md) mít vylepšení zabezpečení, jak je popsáno v [funkce zabezpečení v CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 [out]`buffer`  
 Umístění úložiště pro vstupní řetězec.  
  
 [v]`sizeInCharacters`  
 Velikost vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `buffer` v případě úspěchu. A `NULL` ukazatel označuje podmínku chyby nebo end souboru. Použití [ferror –](../../c-runtime-library/reference/ferror.md) nebo [feof –](../../c-runtime-library/reference/feof.md) k určení, které z nich došlo k chybě.  
  
## <a name="remarks"></a>Poznámky  
 `gets_s` Funkce přečte řádek z standardní vstupní proud `stdin` a uloží jej do `buffer`. Tento řádek představuje všechny znaky do a včetně první znak nového řádku (\n). `gets_s`potom nahradí znak nového řádku znak hodnoty null (\0) před vrácením řádku. Naopak `fgets_s` funkce uchovává znak nového řádku.  
  
 Pokud je první přečtený znak znakem konce souboru, je na začátek parametru `buffer` uložen znak null a je vrácena hodnota `NULL`.  
  
 `_getws`široká charakterová verze `gets_s`; její argument a návratové hodnoty jsou široká charakterová řetězce.  
  
 Pokud `buffer` je `NULL` nebo `sizeInCharacters` je menší než nebo rovna nule, nebo pokud vyrovnávací paměť je příliš malá, aby obsahovat vstupní řádku a null ukončovací znak, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [parametr Ověření](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `NULL` a nastavte errno na `ERANGE`.  
  
 V jazyce C++ pomocí těchto funkcí se zjednodušilo díky šabloně přetížení; přetížení automaticky odvození délka vyrovnávací paměti (takže není nutné zadat argument velikost) a starší, nezabezpečené funkce můžou automaticky nahradit se svými protějšky novější a zabezpečené. Další informace najdete v tématu [přetížení zabezpečení šablony](../../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`gets_s`|\<stdio.h >|  
|`_getws`|\<stdio.h > nebo \<wchar.h >|  
  
 Konzole není podporována v [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Standardní datový proud obslužných rutin, které jsou spojeny s konzolou –`stdin`, `stdout`, a `stderr`– C běhové funkce je mohli používat, musí být přesměrována [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] aplikace. Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../../c-runtime-library/stream-i-o.md)   
 [Získá _getws –](../../c-runtime-library/gets-getws.md)   
 [fgets –, fgetws –](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs –, fputws –](../../c-runtime-library/reference/fputs-fputws.md)   
 [Vloží _putws –](../../c-runtime-library/reference/puts-putws.md)