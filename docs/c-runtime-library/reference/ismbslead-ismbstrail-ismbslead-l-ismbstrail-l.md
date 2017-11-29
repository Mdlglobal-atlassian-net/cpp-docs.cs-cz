---
title: "_ismbslead –, _ismbstrail –, _ismbslead_l –, _ismbstrail_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbstrail
- _ismbslead_l
- _ismbslead
- _ismbstrail_l
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
- _ismbslead
- ismbs
- ismbslead_l
- _ismbs
- ismbstrail_l
- ismbslead
- _ismbstrail
- _ismbstrail_l
- ismbstrail
- _ismbslead_l
dev_langs: C++
helpviewer_keywords:
- ismbstrail function
- _ismbslead function
- ismbslead function
- ismbslead_l function
- _ismbstrail function
- _ismbslead_l function
- ismbstrail_l function
- _ismbstrail_l function
ms.assetid: 86d2cd7a-3cff-443a-b713-14cc17a231e9
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c895deff6a855a6ccc19f9816d359476907c2f22
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ismbslead-ismbstrail-ismbsleadl-ismbstraill"></a>_ismbslead, _ismbstrail, _ismbslead_l, _ismbstrail_l
Provede kontextová testy pro řetězec vícebajtových znaků úvodní bajty a druhé bajty a určuje, zda ukazatel daného podřetězce odkazuje na úvodní bajt nebo druhý bajt.  
  
> [!IMPORTANT]
>  Toto rozhraní API nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime. Další informace najdete v tématu [CRT – funkce není podporována s /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbslead(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbstrail(  
   const unsigned char *str,  
   const unsigned char *current   
);  
int _ismbslead_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
int _ismbstrail_l(  
   const unsigned char *str,  
   const unsigned char *current,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `str`  
 Ukazatel na začátek řetězec nebo předchozí známé úvodní bajt.  
  
 `current`  
 Ukazatel na pozici v řetězec, který má být testována.  
  
 `locale`  
 Národní prostředí, které se má použít  
  
## <a name="return-value"></a>Návratová hodnota  
 `_ismbslead`Vrátí hodnotu -1, pokud znak je úvodní bajt a `_ismbstrail` vrátí hodnotu -1, pokud znak je druhý bajt. Pokud vstupní řetězce jsou platné, ale nejsou vedoucí bajt nebo bajt, vrátí tato funkce nula. Pokud je buď argument `NULL`, obslužná rutina neplatný parametr je vyvolána, jak je popsáno v [ověření parametru](../../c-runtime-library/parameter-validation.md). Pokud je povoleno spuštění chcete-li pokračovat, tyto funkce vracejí `NULL` a nastavte `errno` k `EINVAL`.  
  
## <a name="remarks"></a>Poznámky  
 `_ismbslead`a `_ismbstrail` pomalejší, než `_ismbblead` a `_ismbbtrail` verze protože kontext řetězec berou v úvahu.  
  
 Verze tyto funkce, které mají `_l` příponu jsou shodné s tím rozdílem, že pro jejich chování závislých na národním prostředí používají národní prostředí, je předaná místo aktuální národní prostředí. Další informace najdete v tématu [národního prostředí](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|Nepovinné hlavičkové|  
|-------------|---------------------|---------------------|  
|`_ismbslead`|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|  
|`_ismbstrail`|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|  
|`_ismbslead_l`|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|  
|`_ismbstrail_l`|\<Mbctype.h > nebo \<mbstring.h >|\<ctype.h >, * \<Limits.h – >, \<stdlib.h >|  
  
 \*Pro manifest konstanty podmínky testu.  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace znaků](../../c-runtime-library/character-classification.md)   
 [_ismbc – rutiny](../../c-runtime-library/ismbc-routines.md)   
 [je, isw – rutiny](../../c-runtime-library/is-isw-routines.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)