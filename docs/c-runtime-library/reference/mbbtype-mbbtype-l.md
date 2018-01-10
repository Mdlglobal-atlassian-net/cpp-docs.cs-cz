---
title: "_mbbtype –, _mbbtype_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbbtype
- _mbbtype_l
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
- _mbbtype_l
- mbbtype
- mbbtype_l
- _mbbtype
dev_langs: C++
helpviewer_keywords:
- _mbbtype function
- _mbbtype_l function
- mbbtype function
- mbbtype_l function
ms.assetid: b8e34b40-842a-4298-aa39-0bd2d8e51c2a
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae66b1c0765f496dcfe460c4ea7ff4f84e9333ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbbtype-mbbtypel"></a>_mbbtype, _mbbtype_l
Vrátí typ bajtů podle předchozích bajtů.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _mbbtype(  
   unsigned char c,  
   int type   
);  
int _mbbtype_l(  
   unsigned char c,  
   int type,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Znak, který se má testovat.  
  
 `type`  
 Typ bajtů, které chcete otestovat.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `_mbbtype`Vrátí typ bajtů v řetězci. Toto rozhodnutí je kontextová jako zadanou hodnotou `type`, který poskytuje testovací podmínky řízení. `type`je typ předchozí bajtů v řetězci. Manifestu konstanty v následující tabulce jsou definovány v Mbctype.h.  
  
|Hodnota`type`|`_mbbtype`testování pro|Návratová hodnota|`c`|  
|---------------------|--------------------------|------------------|---------|  
|Libovolná hodnota s výjimkou 1|Platný jednoho bajtu nebo úvodní bajt|`_MBC_SINGLE` (0)|Jeden bajt (0x20 - 0x7E, 0xA1 - 0xDF)|  
|Libovolná hodnota s výjimkou 1|Platný jednoho bajtu nebo úvodní bajt|`_MBC_LEAD` (1)|Vést bajt vícebajtových znaků (0x81 - 0x9F, 0xE0 - 0xFC)|  
|Libovolná hodnota s výjimkou 1|Platnou bajtovou jednobajtové nebo nepovedou|`_MBC_ILLEGAL`<br /><br /> ( -1)|Neplatný znak (všechny hodnota s výjimkou 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|  
|1|Platný bajt|`_MBC_TRAIL` (2)|Koncové bajt vícebajtových znaků (0x40 - 0x7E, 0x80 - 0xFC)|  
|1|Platný bajt|`_MBC_ILLEGAL`<br /><br /> ( -1)|Neplatný znak (všechny hodnota s výjimkou 0x20 - 0x7E, 0xA1 - 0xDF, 0x81 - 0x9F, 0xE0 - 0xFC|  
  
## <a name="remarks"></a>Poznámky  
 `_mbbtype` Funkce určuje typ bajtů v vícebajtových znaků. Pokud hodnota `type` je jakákoli hodnota s výjimkou 1, `_mbbtype` testů pro platný jednobajtové nebo nepovedou bajt vícebajtových znaků. Pokud hodnota `type` je 1, `_mbbtype` testů pro platný bajt vícebajtových znaků.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. `_mbbtype` Verze této funkce používá aktuální národní prostředí pro toto chování závislých na národním prostředí; `_mbbtype_l` verze je stejná s tím rozdílem, že ji, použijte parametr národního prostředí, je předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 V dřívějších verzích `_mbbtype` nazýval `chkctype`. Nový kód, použijte `_mbbtype` místo.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_mbbtype`|\<Mbstring.h >|\<Mbctype.h > *|  
|`_mbbtype_l`|\<Mbstring.h >|\<Mbctype.h > *|  
  
 \*Definice manifestu konstanty, které se používají jako návratové hodnoty.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)