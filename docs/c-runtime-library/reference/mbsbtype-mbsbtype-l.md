---
title: "_mbsbtype –, _mbsbtype_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsbtype_l
- _mbsbtype
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
- mbsbtype
- mbsbtype_l
- _mbsbtype_l
- _mbsbtype
dev_langs: C++
helpviewer_keywords:
- _mbsbtype function
- mbsbtype function
- _mbsbtype_l function
- mbsbtype_l function
ms.assetid: 0d5dd91a-d32d-4f98-ac57-98dfc9e98eac
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 05c106136c36d09b06e5b168a0c582b87c306d93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mbsbtype-mbsbtypel"></a>_mbsbtype, _mbsbtype_l
Vrátí typ bajtů v řetězci.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _mbsbtype(  
   const unsigned char *mbstr,  
   size_t count   
);  
int _mbsbtype_l(  
   const unsigned char *mbstr,  
   size_t count,  
   _locale_t locale   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mbstr`  
 Adresa posloupnosti více-bajtové znaky.  
  
 `count`  
 Posun bajtů, z hlavičky řetězce.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_mbsbtype`a `_mbsbtype_l` vrací celočíselnou hodnotu udávající výsledek testu na zadané bajtové. Manifestu konstanty v následující tabulce jsou definovány v Mbctype.h.  
  
|Návratová hodnota|Byte – typ|  
|------------------|---------------|  
|`_MBC_SINGLE` (0)|Znakovou. Například v znaková stránka 932 `_mbsbtype` vrátí hodnotu 0, pokud zadaný bajt je v rozsahu 0x20-0x7E nebo 0xA1 - 0xDF.|  
|`_MBC_LEAD` (1)|Vést bajt vícebajtových znaků. Například v znaková stránka 932 `_mbsbtype` vrátí hodnotu 1, pokud zadaný bajt je v rozsahu 0x81-0x9F nebo 0xE0 - 0xFC.|  
|`_MBC_TRAIL` (2)|Koncové bajt vícebajtových znaků. Například v znaková stránka 932 `_mbsbtype` vrátí 2, pokud zadaný bajt je v rozsahu 0x40-0x7E nebo 0x80 - 0xFC.|  
|`_MBC_ILLEGAL` (-1)|`NULL`řetězec, neplatný znak nebo `NULL` nalezeno před bajtů na posunu bajtů `count` v `mbstr`.|  
  
## <a name="remarks"></a>Poznámky  
 `_mbsbtype` Funkce určuje typ jednoho bajtu řetězce vícebajtových znaků. Funkce prozkoumá pouze bajtů na posunu `count` v `mbstr`, ignoruje před zadané bajtové neplatné znaky.  
  
 Výstupní hodnota je ovlivňován nastavením `LC_CTYPE` kategorie nastavení národního prostředí; viz [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) Další informace. Verze této funkce bez `_l` příponu používá aktuální národní prostředí pro toto chování závislých na národním prostředí; verzi s `_l` přípona se shoduje s tím rozdílem, že ji, použijte parametr národního prostředí předaná místo. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
 Pokud je vstupní řetězec `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud chcete pokračovat, je povoleno spuštění `errno` je nastaven na `EINVAL` a funkce vrátí hodnotu `_MBC_ILLEGAL`.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_mbsbtype`|\<Mbstring.h >|\<Mbctype.h > *|  
|`_mbsbtype_l`|\<Mbstring.h >|\<Mbctype.h > *|  
  
 \*Pro manifest konstanty použít jako návratové hodnoty.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)