---
title: "_ismbcalnum –, _ismbcalnum_l –, _ismbcalpha –, _ismbcalpha_l –, _ismbcdigit –, _ismbcdigit_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcalpha
- _ismbcalnum
- _ismbcdigit
- _ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _ismbcdigit
- ismbcalnum_l
- _ismbcdigit_l
- _ismbcalpha
- ismbcalnum
- ismbcdigit
- ismbcalpha
- _ismbcalnum_l
- _ismbcalnum
- ismbcdigit_l
dev_langs: C++
helpviewer_keywords:
- ismbcalpha function
- _ismbcalnum function
- ismbcdigit_l function
- _ismbcalnum_l function
- _ismbcdigit function
- ismbcalnum function
- _ismbcalpha_l function
- ismbcdigit function
- _ismbcalpha function
- _ismbcdigit_l function
- ismbcalnum_l function
- ismbcalpha_l function
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 40566a3f4f6855da3a7ee7d122357f392d234ff0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ismbcalnum-ismbcalnuml-ismbcalpha-ismbcalphal-ismbcdigit-ismbcdigitl"></a>_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
Zkontroluje, jestli je alfanumerické vícebajtových znaků, alpha nebo znak číslice.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbcalnum  
(  
   unsigned int c   
);  
int _ismbcalnum_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcalpha  
(  
   unsigned int c   
);  
int _ismbcalpha_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcdigit  
(  
   unsigned int c   
);  
int _ismbcdigit_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být testována.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí nenulovou hodnotu, pokud znak splňuje podmínky testu nebo 0, pokud neexistuje. Pokud `c`< = 255 a existuje odpovídající `_ismbb` rutiny (například `_ismbcalnum` odpovídá `_ismbbalnum`), výsledkem je vrácenou hodnotu odpovídající `_ismbb` rutiny.  
  
## <a name="remarks"></a>Poznámky  
 Každý z těchto rutin testy dané vícebajtových znaků pro danou podmínku.  
  
 Verze tyto funkce s `_l` příponu jsou shodné s tím rozdílem, že používají národní prostředí předaná místo aktuální národní prostředí pro jejich chování závislých na národním prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
|Rutina|Test stavu|Příklad kódu stránka 932|  
|-------------|--------------------|---------------------------|  
|`_ismbcalnum,_ismbcalnum_l`|Alfanumerické|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k písmenu anglické ASCII: obsahuje příklady `_ismbcdigit` a `_ismbcalpha`.|  
|`_ismbcalpha,_ismbcalpha_l`|Abecedy|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové k písmenu anglické ASCII: 0x41 < =`c`< = 0x5A nebo 0x61 < =`c`< = 0x7A; nebo katakana písmeno: 0xA6 < =`c`< = 0xDF.|  
|`_ismbcdigit,_ismbcdigit`|Číslice|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové číslic ASCII: 0x30 < =`c`< = 0x39.|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbcalnum,_ismbcalnum_l`|\<Mbstring.h >|  
|`_ismbcalpha,_ismbcalpha_l`|\<Mbstring.h >|  
|`_ismbcdigit,_ismbcdigit_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)