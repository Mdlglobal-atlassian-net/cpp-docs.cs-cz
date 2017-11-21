---
title: "_ismbcgraph –, _ismbcgraph_l –, _ismbcprint –, _ismbcprint_l –, _ismbcpunct –, _ismbcpunct_l –, _ismbcblank, _ismbcblank_l, _ismbcspace –, _ismbcspace_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbcpunct_l
- _ismbcblank
- _ismbcprint
- _ismbcgraph_l
- _ismbcblank_l
- _ismbcpunct
- _ismbcprint_l
- _ismbcspace_l
- _ismbcspace
- _ismbcgraph
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
- _ismbcspace
- _ismbcgraph
- _ismbcpunct
- ismbcspace_l
- ismbcgraph
- _ismbcgraph_l
- _ismbcprint
- _ismbcspace_l
- ismbcprint
- ismbcgraph_l
- ismbcspace
- ismbcpunct
dev_langs: C++
helpviewer_keywords:
- ismbcspace_l function
- _ismbcprint_l function
- ismbcspace function
- ismbcpunct function
- _ismbcspace_l function
- _ismbcprint function
- ismbcprint function
- _ismbcgraph function
- ismbcgraph_l function
- _ismbcpunct_l function
- ismbcpunct_l function
- ismbcprint_l function
- _ismbcpunct function
- ismbcgraph function
- _ismbcgraph_l function
- _ismbcspace function
ms.assetid: 8e0a5f47-ba64-4411-92a3-3c525d16e3be
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b2079cb0b00513babd6dc2d5b6c91e82675acc74
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ismbcgraph-ismbcgraphl-ismbcprint-ismbcprintl-ismbcpunct-ismbcpunctl-ismbcblank-ismbcblankl-ismbcspace-ismbcspacel"></a>_ismbcgraph, _ismbcgraph_l, _ismbcprint, _ismbcprint_l, _ismbcpunct, _ismbcpunct_l, _ismbcblank, _ismbcblank_l, _ismbcspace, _ismbcspace_l
Určuje, zda znak je znak grafické, zobrazení znak, interpunkční znaménko nebo znak mezery.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu[CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbcgraph(  
   unsigned int c   
);  
int _ismbcgraph_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcprint(  
   unsigned int c   
);  
int _ismbcprint_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcpunct(  
   unsigned int c  
);  
int _ismbcpunct_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcblank(  
   unsigned int c   
);  
int _ismbcblank_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcspace(  
   unsigned int c   
);  
int _ismbcspace_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který má být určen.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Všechny tyto rutiny vrátí nenulovou hodnotu, pokud znak splňuje podmínky testu, nebo 0, pokud neexistuje. Pokud `c` < = 255 a existuje odpovídající `_ismbb` rutiny (například `_ismbcalnum` odpovídá `_ismbbalnum`), výsledkem je vrácenou hodnotu odpovídající `_ismbb` rutiny.  
  
 Verze tyto funkce jsou identické, s tím rozdílem, že ty, které mají `_l` používat příponu národní prostředí, je předaná pro jejich chování závislých na národním prostředí, místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="remarks"></a>Poznámky  
 Každá z těchto funkcí testuje dané vícebajtových znaků pro danou podmínku.  
  
|Rutina|Test stavu|Příklad kódu stránka 932|  
|-------------|--------------------|---------------------------|  
|`_ismbcgraph`|Obrázek|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové jakémukoli ASCII nebo katakana tisknutelná znaku kromě () mezer.|  
|`_ismbcprint`|Tisknutelná|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové libovolný ASCII nebo katakana tisknutelná znak včetně () mezer.|  
|`_ismbcpunct`|Interpunkční znaménka|Vrátí nenulové hodnoty v případě a pouze v případě `c` je reprezentace jednobajtové žádné ASCII nebo katakana interpunkční znaménko.|  
|`_ismbcblank`|Místo nebo vodorovné karta|Vrátí nenulové hodnoty v případě a pouze v případě `c` je místo nebo horizontální tabulátor: `c`= 0x20 nebo `c`= 0x09.|  
|`_ismbcspace`|Prázdné znaky|Vrátí nenulové hodnoty v případě a pouze v případě `c` je prázdný znak: `c`= 0x20 nebo 0x09 < =`c`< = 0x0D.|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbcgraph`|\<Mbstring.h >|  
|`_ismbcgraph_l`|\<Mbstring.h >|  
|`_ismbcprint`|\<Mbstring.h >|  
|`_ismbcprint_l`|\<Mbstring.h >|  
|`_ismbcpunct`|\<Mbstring.h >|  
|`_ismbcpunct_l`|\<Mbstring.h >|  
|`_ismbcblank`|\<Mbstring.h >|  
|`_ismbcblank_l`|\<Mbstring.h >|  
|`_ismbcspace`|\<Mbstring.h >|  
|`_ismbcspace_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)