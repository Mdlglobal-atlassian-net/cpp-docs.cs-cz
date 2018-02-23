---
title: "isalnum –, iswalnum –, _isalnum_l –, _iswalnum_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _iswalnum_l
- _isalnum_l
- iswalnum
- isalnum
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
- _istalnum_l
- _iswalnum_l
- iswalnum
- _isalnum_l
- isalnum
- _istalnum
dev_langs:
- C++
helpviewer_keywords:
- _istalnum function
- _ismbcalnum_l function
- iswalnum function
- isalnum function
- istalnum function
- _isalnum_l function
- _istalnum_l function
- _iswalnum_l function
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f71ab6a960dbc92c4e6d8399e833f2ddf0e2ac1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="isalnum-iswalnum-isalnuml-iswalnuml"></a>isalnum, iswalnum, _isalnum_l, _iswalnum_l
Určuje, zda celé reprezentuje alfanumerický znak.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int isalnum(   
   int c   
);  
int iswalnum(   
   wint_t c   
);  
int _isalnum_l(   
   int c,  
   _locale_t locale  
);  
int _iswalnum_l(   
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
 Všechny tyto rutiny vrátí nenulové hodnoty, pokud `c` je konkrétní reprezentace alfanumerický znak. `isalnum` vrátí nenulovou hodnotu, pokud buď `isalpha` nebo `isdigit` je nenulové hodnoty pro `c`, to znamená, pokud `c` je v rámci rozsahu A - Z, a - z nebo 0 - 9. `iswalnum` vrátí nenulovou hodnotu, pokud buď `iswalpha` nebo `iswdigit` je nenulové hodnoty pro `c`. Všechny tyto rutiny vrátí hodnotu 0, pokud `c` nesplňuje podmínky testu.  
  
 Verze tyto funkce, které mají `_l` příponu použijte parametr národního prostředí, je předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Chování `isalnum` a `_isalnum_l` není definován, pokud `c` není EOF nebo v rozsahu 0 až 0xFF (včetně). V případě použití knihovny ladění CRT a `c` není jednou z těchto hodnot, funkce raise kontrolní výrazy.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istalnum`|`isalnum`|[_ismbcalnum](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswalnum`|  
|`_istalnum_l`|`_isalnum_l`|`_ismbcalnum_l`|`_iswalnum_l`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`isalnum`|\<ctype.h>|  
|`iswalnum`|\<ctype.h > nebo \<wchar.h >|  
|`_isalnum_l`|\<ctype.h>|  
|`_iswalnum_l`|\<ctype.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [is, isw – rutiny](../../c-runtime-library/is-isw-routines.md)