---
title: "wctype – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wctype
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
apitype: DLLExport
f1_keywords: wctype
dev_langs: C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: daae662a39d012418b5cd178e26d731dbca1e715
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wctype"></a>wctype
Určuje pravidla klasifikace pro široká charakterová kódy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wctype_t wctype(  
   const char * property   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `property`  
 Vlastnost řetězec.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud `LC_CTYPE` kategorie aktuální národní prostředí nedefinuje pravidla klasifikace, jejíž název odpovídá řetězci vlastnost `property`, funkce vrátí hodnotu nula. Jinak vrátí nenulovou hodnotu vhodné pro použití jako druhý argument pro následné volání [towctrans –](../../c-runtime-library/reference/towctrans.md).  
  
## <a name="remarks"></a>Poznámky  
 Funkce určuje pravidla klasifikace pro široká charakterová kódy. Následující páry volání mají stejné chování ve všech národních prostředí (ale implementace můžete definovat pravidla další klasifikace i v národním prostředí "C"):  
  
|Funkce|Stejné jako|  
|--------------|-------------|  
|`iswalnum(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alnum" ) )`|  
|`iswalpha(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alpha" ) )`|  
|`iswcntrl(`  `c`  `)`|`iswctype(`  `c` `, wctype( "cntrl" ) )`|  
|`iswdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "digit" ) )`|  
|`iswgraph(`  `c`  `)`|`iswctype(`  `c` `, wctype( "graph" ) )`|  
|`iswlower(`  `c`  `)`|`iswctype(`  `c` `, wctype( "lower" ) )`|  
|`iswprint(`  `c`  `)`|`iswctype(`  `c` `, wctype( "print" ) )`|  
|`iswpunct(`  `c`  `)`|`iswctype(`  `c` `, wctype( "punct" ) )`|  
|`iswspace(`  `c`  `)`|`iswctype(`  `c` `, wctype( "space" ) )`|  
|`iswupper(`  `c`  `)`|`iswctype(`  `c` `, wctype( "upper" ) )`|  
|`iswxdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "xdigit" ) )`|  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`wctype`|\<wctype.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [setlocale –, _wsetlocale –](../../c-runtime-library/reference/setlocale-wsetlocale.md)