---
title: "_mbctombb –, _mbctombb_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbctombb_l
- _mbctombb
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
- _mbctombb_l
- _mbctombb
- mbctombb_l
- mbctombb
dev_langs: C++
helpviewer_keywords:
- _mbctombb function
- mbctombb_l function
- mbctombb function
- _mbctombb_l function
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f358376a16d811274978ccc730268e7cbe806df7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mbctombb-mbctombbl"></a>_mbctombb, _mbctombb_l
Převede na odpovídající vícebajtových znaků jednobajtové dvoubajtové vícebajtových znaků.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
unsigned int _mbctombb(  
   unsigned int c   
);  
unsigned int _mbctombb_l(  
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
 V případě úspěšného `_mbctombb` a `_mbctombb_l` vrátí jednobajtové znak, který odpovídá `c`; v opačném případě vrátí `c`.  
  
## <a name="remarks"></a>Poznámky  
 `_mbctombb` a `_mbctombb_l` funkce převést na odpovídající vícebajtových znaků jednobajtové dané vícebajtových znaků. Znaky musí odpovídat jednobajtové znaky v rozsahu 0x20-0x7E nebo 0xA1 - 0xDF má být převeden.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze této funkce bez `_l` příponu používá aktuální národní prostředí pro toto chování závislých na národním prostředí; verzi s `_l` přípona se shoduje s tím rozdílem, že ji, použijte parametr národního prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V předchozích verzích `_mbctombb` byla volána `zentohan`. Místo nich se používá `_mbctombb`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_mbctombb`|\<Mbstring.h >|  
|`_mbctombb_l`|\<Mbstring.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Převod dat](../../c-runtime-library/data-conversion.md)   
 [_mbbtombc –, _mbbtombc_l –](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [_mbcjistojms –, _mbcjistojms_l –, _mbcjmstojis –, _mbcjmstojis_l –](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [_mbctohira –, _mbctohira_l –, _mbctokata –, _mbctokata_l –](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [_mbctolower –, _mbctolower_l –, _mbctoupper –, _mbctoupper_l –](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)