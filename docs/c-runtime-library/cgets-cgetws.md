---
title: "_cgets –, _cgetws – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _cgetws
- _cgets
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- cgetws
- _cgetws
- _cgets
dev_langs:
- C++
helpviewer_keywords:
- _cgetws function
- strings [C++], getting from console
- console, getting strings from
- _cgets function
- cgetws function
- cgets function
ms.assetid: 4d5e134a-58c3-4f62-befd-5d235b0212f4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 81ce9e8144fc280cc8192696178648776c78f033
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="cgets-cgetws"></a>_cgets, _cgetws
Získá řetězec znaků z konzoly. Bezpečnější verze tyto funkce jsou k dispozici. v tématu [_cgets_s –, _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Tyto funkce jsou zastaralé. Od verze sady Visual Studio 2015, nejsou k dispozici v CRT. Zabezpečené verze těchto funkcí, _cgets_s – a _cgetws_s –, jsou stále k dispozici. Informace o těchto funkcích alternativní najdete v tématu [_cgets_s –, _cgetws_s –](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
char *_cgets(   
   char *buffer   
);  
wchar_t *_cgetws(  
   wchar_t *buffer  
);  
template <size_t size>  
char *_cgets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_cgetws(  
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parametry  
 `buffer`  
 Umístění úložiště pro data.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_cgets` a `_cgetws` vrátit ukazatel na začátek řetězci `buffer[2]`. Pokud `buffer` je `NULL`, tyto funkce vyvolat obslužnou rutinu neplatný parametr, jak je popsáno v [ověření parametru](../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, že budou vracet `NULL` a nastavte `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 Tyto funkce číst řetězec znaků z konzoly a uložení řetězec a jeho délka v umístění, na kterou odkazuje `buffer`. `buffer` Parametr musí být ukazatel na pole znaků. První prvek pole, `buffer[0]`, musí obsahovat maximální délku (ve znacích) řetězec, který má být pro čtení. Pole musí obsahovat dostatečný počet elementů k uchování řetězec ukončující znak hodnoty null (\0) a 2 Další bajtů. Funkce přečte znaky, dokud znaků CR vrátit-odřádkování kombinaci (CR-LF) nebo zadaný počet znaků je pro čtení. Řetězec je uložen počínaje `buffer[2]`. Pokud funkce přečte znaky CR LF, ukládá znak hodnoty null ('\0'). Funkce pak uloží skutečná délka řetězce v druhý prvkem pole `buffer[1]`.  
  
 Protože všechny úpravy klíče jsou aktivní, kdy `_cgets` nebo `_cgetws` je volána, když v konzole okna, stisknutím klávesy F3 opakuje poslední zadané položky.  
  
 V jazyce C++ tyto funkce mají šabloně přetížení, které vyvolání novější a zabezpečené svými protějšky tyto funkce. Další informace najdete v tématu [přetížení zabezpečení šablony](../c-runtime-library/secure-template-overloads.md).  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina Tchar.h|_UNICODE a _MBCS nejsou definovány.|_MBCS definováno|_UNICODE definováno|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_cgetts`|`_cgets`|`_cgets`|`_cgetws`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_cgets`|\<conio.h>|  
|`_cgetws`|\<conio.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Příklad  
  
```  
// crt_cgets.c  
// compile with: /c /W3  
// This program creates a buffer and initializes  
// the first byte to the size of the buffer. Next, the  
// program accepts an input string using _cgets and displays  
// the size and text of that string.  
  
#include <conio.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char buffer[83] = { 80 };  // Maximum characters in 1st byte  
   char *result;  
  
   printf( "Input line of text, followed by carriage return:\n");  
  
   // Input a line of text:  
   result = _cgets( buffer ); // C4996  
   // Note: _cgets is deprecated; consider using _cgets_s  
   if (!result)  
   {  
      printf( "An error occurred reading from the console:"  
              " error code %d\n", errno);  
   }  
   else  
   {     
      printf( "\nLine length = %d\nText = %s\n",  
              buffer[1], result );  
   }  
}  
```  
  
```Output  
  
      A line of input.Input line of text, followed by carriage return:  
Line Length = 16  
Text = A line of input.  
```  
  
## <a name="see-also"></a>Viz také  
 [I/O konzoly a portu](../c-runtime-library/console-and-port-i-o.md)   
 [_getch, _getwch](../c-runtime-library/reference/getch-getwch.md)