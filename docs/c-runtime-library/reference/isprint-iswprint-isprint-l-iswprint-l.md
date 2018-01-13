---
title: "isprint –, iswprint –, _isprint_l –, _iswprint_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswprint
- isprint
- _isprint_l
- _iswprint_l
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswprint
- _istprint
- isprint
dev_langs: C++
helpviewer_keywords:
- _istprint function
- iswprint function
- _iswprint_l function
- isprint_l function
- istprint function
- isprint function
- iswprint_l function
- _isprint_l function
ms.assetid: a8bbcdb0-e8d0-4d8c-ae4e-56d3bdee6ca3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6ab79ddcf6232e8c3d4345cc1bc3cda7c7deb1dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isprint-iswprint-isprintl-iswprintl"></a>isprint, iswprint, _isprint_l, _iswprint_l
Určuje, zda celé reprezentuje tisknutelná znak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int isprint(  
   int c   
);  
int iswprint(  
   wint_t c   
);  
int _isprint_l(  
   int c,  
   _locale_t locale  
);  
int _iswprint_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Celé číslo pro testování.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí nenulové hodnoty, pokud `c` je konkrétní reprezentace tisknutelná znaku. `isprint`vrátí nenulovou hodnotu, pokud `c` je tisknutelná znaků – to zahrnuje znak mezery (0x20 - 0x7E). `iswprint`vrátí nenulovou hodnotu, pokud `c` je tisknutelná široká znaková – to zahrnuje celý znak místa. Všechny tyto rutiny vrátí hodnotu 0, pokud `c` nesplňuje podmínky testu.  
  
 Výsledek testu podmínky pro tyto funkce závisí na `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce, které nemají `_l` příponu využívání aktuální národní prostředí pro chování všech závislých na národním prostředí, verze, které mají `_l` příponu jsou shodné s tím rozdílem, že používají národní prostředí, je předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Chování `isprint` a `_isprint_l` není definován, pokud `c` není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a `c` není jednou z těchto hodnot, funkce raise kontrolní výrazy.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definované|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|**_** `istprint`|`isprint`|[_ismbcprint –](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswprint`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`isprint`|\<ctype.h >|  
|`iswprint`|\<ctype.h > nebo \<wchar.h >|  
|`_isprint_l`|\<ctype.h >|  
|`_iswprint_l`|\<ctype.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)