---
title: "_mbctohira –, _mbctohira_l –, _mbctokata –, _mbctokata_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbctohira
- _mbctohira_l
- _mbctokata
- _mbctokata_l
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
- _mbctokata
- mbctohira
- _mbctohira
- _mbctohira_l
- mbctokata
- mbctokata_l
- mbctohira_l
- _mbctokata_l
dev_langs: C++
helpviewer_keywords:
- _mbctokata function
- _mbctokata_l function
- _mbctohira_l function
- mbctohira_l function
- mbctohira function
- mbctokata_l function
- _mbctohira function
- mbctokata function
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0a398e2d0b55a8c3292a77ba957982fa5a5e21f8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbctohira-mbctohiral-mbctokata-mbctokatal"></a>_mbctohira, _mbctohira_l, _mbctokata, _mbctokata_l
Převede hiragana a katakana znaků.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _mbctohira(  
   unsigned int c   
);  
unsigned int _mbctohira_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctokata(  
   unsigned int c   
);  
unsigned int _mbctokata_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Vícebajtové znakové převést.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Každá z těchto funkcí vrátí znak převedený `c`, pokud je to možné. V opačném případě vrátí znak `c` beze změny.  
  
## <a name="remarks"></a>Poznámky  
 `_mbctohira` a `_mbctokata` funkce testování znak `c` a pokud je to možné, použijte jednu z následujících převody.  
  
|Rutiny|Převede|  
|--------------|--------------|  
|`_mbctohira,_mbctohira_l`|Vícebajtových katakana k vícebajtové hiragana.|  
|`_mbctokata,_mbctokata_l`|Vícebajtových hiragana na více-bajtové znaky katakana.|  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze tyto funkce jsou identické, s tím rozdílem, že ty, které nejsou mít `_l` příponu použít aktuální národní prostředí pro toto chování závislých na národním prostředí a ty, které mají `_l` příponu, použijte parametr národního prostředí to je Předaná. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V dřívějších verzích `_mbctohira` nazýval `jtohira` a `_mbctokata` nazýval `jtokata`. Nový kód použijte nové názvy.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbctohira`|\<Mbstring.h >|  
|`_mbctohira_l`|\<Mbstring.h >|  
|`_mbctokata`|\<Mbstring.h >|  
|`_mbctokata_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_mbcjistojms –, _mbcjistojms_l –, _mbcjmstojis –, _mbcjmstojis_l –](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [_mbctolower –, _mbctolower_l –, _mbctoupper –, _mbctoupper_l –](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)   
 [_mbctombb –, _mbctombb_l –](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)