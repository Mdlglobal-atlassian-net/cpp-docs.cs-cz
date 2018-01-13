---
title: "IsDigit –, iswdigit –, _isdigit_l –, _iswdigit_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isdigit_l
- iswdigit
- _iswdigit_l
- isdigit
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
- _iswdigit_l
- _isdigit_l
- iswdigit
- isdigit
- _istdigit
- _istdigit_l
dev_langs: C++
helpviewer_keywords:
- iswdigit function
- iswdigit_l function
- _iswdigit_l function
- _istdigit_l function
- _istdigit function
- istdigit function
- isdigit function
- isdigit_l function
- _ismbcdigit_l function
- _isdigit_l function
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84b2293114acd31d0baf1f3a595deba9247d6120
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isdigit-iswdigit-isdigitl-iswdigitl"></a>isdigit, iswdigit, _isdigit_l, _iswdigit_l
Určuje, zda celé představuje znak desetinných číslic.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int isdigit(   
   int c   
);  
int iswdigit(   
   wint_t c   
);  
int _isdigit_l(   
   int c,  
   _locale_t locale  
);  
int _iswdigit_l(   
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
 Všechny tyto rutiny vrátí nenulové hodnoty, pokud `c` je konkrétní reprezentace znaku desetinných číslic. `isdigit`vrátí nenulovou hodnotu, pokud `c` je desítková číslice (0 - 9). `iswdigit`vrátí nenulovou hodnotu, pokud `c` je široké znak, který odpovídá znak desetinných číslic. Všechny tyto rutiny vrátí hodnotu 0, pokud `c` nesplňuje podmínky testu.  
  
 Verze tyto funkce, které mají `_l` používat příponu národní prostředí, je předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Chování `isdigit` a `_isdigit_l` není definován, pokud `c` není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a `c` není jednou z těchto hodnot, funkce raise kontrolní výrazy.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istdigit`|`isdigit`|[_ismbcdigit –](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswdigit`|  
|`_istdigit_l`|`_isdigit_l`|[_ismbcdigit_l –](../../c-runtime-library/reference/ismbcalnum-functions.md)|`_iswdigit_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`isdigit`|\<ctype.h >|  
|`iswdigit`|\<ctype.h > nebo \<wchar.h >|  
|`_isdigit_l`|\<ctype.h >|  
|`_iswdigit_l`|\<ctype.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)