---
title: Získá _getws – | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs:
- C++
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a597ad1a72f903d08e848727045e05bf014879b1
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2018
---
# <a name="gets-getws"></a>gets, _getws
Získá řádek z `stdin` datového proudu. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [gets_s –, _getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od verze sady Visual Studio 2015, nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, gets_s – a _getws_s –, jsou stále k dispozici. Informace o těchto funkcích alternativní najdete v tématu [gets_s –, _getws_s –](../c-runtime-library/reference/gets-s-getws-s.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro vstupní řetězec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Její argument vrací, pokud bylo úspěšné. A **NULL** ukazatel označuje podmínku chyby nebo end souboru. Použití [ferror –](../c-runtime-library/reference/ferror.md) nebo [feof –](../c-runtime-library/reference/feof.md) k určení, které z nich došlo k chybě. Pokud `buffer` je **NULL**, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí **NULL** a nastavte errno na `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `gets` Funkce přečte řádek z standardní vstupní proud `stdin` a uloží jej do `buffer`. Tento řádek představuje všechny znaky do a včetně první znak nového řádku (\n). `gets` potom nahradí znak nového řádku znak hodnoty null (\0) před vrácením řádku. Naopak `fgets` funkce uchovává znak nového řádku. `_getws` široká charakterová verze `gets`; její argument a návratové hodnoty jsou široká charakterová řetězce.  
  
> [!IMPORTANT]
>  Protože neexistuje žádný způsob, jak omezit počet znaků číst získá, nedůvěryhodné vstup snadno způsobit přetečení vyrovnávací paměti. Místo nich se používá `fgets`.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`gets`|\<stdio.h>|  
|`_getws`|\<stdio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_gets.c  
// compile with: /WX /W3  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C4996  
   // Danger: No way to limit input to 20 chars.  
   // Consider using gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
 Všimněte si, že vstup delší než 20 znaků přetečení vyrovnávací paměti pro řádek, který se skoro určitě dojít k chybě programu.  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>Viz také  
 [Datový proud vstupně-výstupních operací](../c-runtime-library/stream-i-o.md)   
 [fgets –, fgetws –](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs –, fputws –](../c-runtime-library/reference/fputs-fputws.md)   
 [puts, _putws](../c-runtime-library/reference/puts-putws.md)