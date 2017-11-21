---
title: "ToLower, _tolower –, towlower –, _tolower_l –, _towlower_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _tolower_l
- towlower
- tolower
- _tolower
- _towlower_l
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
- ntdll.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _totlower
- tolower
- _tolower
- towlower
dev_langs: C++
helpviewer_keywords:
- tolower_l function
- _tolower_l function
- totlower function
- string conversion, to different characters
- lowercase, converting to
- tolower function
- string conversion, case
- towlower function
- _tolower function
- _totlower function
- towlower_l function
- case, converting
- characters, converting
- _towlower_l function
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bd7c3fd10461033c6b66a96eecd4d5e6ec5941b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tolower-tolower-towlower-tolowerl-towlowerl"></a>tolower, _tolower, towlower, _tolower_l, _towlower_l
Převádí znak na malá písmena.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`c`  
 Znak, který má převést.  
  
 [v]`locale`  
 Národní prostředí pro překlad specifická pro národní prostředí.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každý z těchto rutin převádí kopii `c` na malá písmena, pokud převod je možné a vrátí výsledek. Je rezervovaný pro označení chybu žádnou návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je to možné a relevantní každý z těchto rutin dané velké písmeno převede na malé písmeno. Case převodu `towlower` je specifický pro národní prostředí. V případě došlo ke změně pouze znaky, které se týkají aktuální národní prostředí. Funkce bez `_l` používat příponu aktuálně nastavené národní prostředí. Verze tyto funkce, které mají `_l` příponu trvat národní prostředí jako parametr a použijte místo aktuálně nastavené národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Aby `_tolower` umožnit očekávané výsledky, [__isascii –](../../c-runtime-library/reference/isascii-isascii-iswascii.md) a [isupper –](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) musí i vrátit nenulové hodnoty.  
  
### <a name="generic-text-routine-mappings"></a>Mapování rutin obecného textu  
  
|Rutina TCHAR.H|_UNICODE & _MBCS není definován|_MBCS definováno|_UNICODE definováno|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l`a `_towlower_l` mít žádná závislost na národním prostředí a nejsou určeny k přímému volání. Jsou k dispozici pro interní použití rozhraním `_totlower_l`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`tolower`|\<ctype.h >|  
|`_tolower`|\<ctype.h >|  
|`towlower`|\<ctype.h > nebo \<wchar.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md) v úvodu.  
  
## <a name="example"></a>Příklad  
 Podívejte se na příklad v [na funkce](../../c-runtime-library/to-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [to – funkce](../../c-runtime-library/to-functions.md)   
 [Národní prostředí](../../c-runtime-library/locale.md)   
 [Výklad sekvencí vícebajtových znaků](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)