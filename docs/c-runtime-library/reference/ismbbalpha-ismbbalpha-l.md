---
title: "_ismbbalpha –, _ismbbalpha_l – | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ismbbalpha
- _ismbbalpha_l
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
- ismbbalpha
- ismbbalpha_l
- _ismbbalpha
- _ismbbalpha_l
dev_langs: C++
helpviewer_keywords:
- ismbbalpha function
- ismbbalpha_l function
- _ismbbalpha function
- _ismbbalpha_l function
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2218d7b563666429aeeed07059b4e32640ffefe2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ismbbalpha-ismbbalphal"></a>_ismbbalpha, _ismbbalpha_l
Určuje, zda je zadaný znak vícebajtové alfa.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
int _ismbbalpha(  
   unsigned int c   
);  
int _ismbbalpha_l(  
   unsigned int c   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `c`  
 Celé číslo má být testována.  
  
 `locale`  
 Národní prostředí použít.  
  
## <a name="return-value"></a>Návratová hodnota  
 `_ismbbalpha`vrátí nenulovou hodnotu, pokud výraz:  
  
```  
isalpha || _ismbbkalnum  
```  
  
 je nenulové hodnoty pro `c`, nebo 0, pokud není. `_ismbbalpha`používá aktuální národní prostředí pro všechna nastavení znak závislých na národním prostředí. `_ismbbalpha_l`se shoduje s tím rozdílem, že používá předaná národní prostředí.  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|`_ismbbalpha`|\<Mbctype.h >|  
|`_ismbbalpha_l`|\<Mbctype.h >|  
  
 Další informace o kompatibilitě, najdete v části [kompatibility](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Knihovny  
 Všechny verze [běhové knihovny jazyka C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Viz také  
 [Klasifikace bajtů](../../c-runtime-library/byte-classification.md)   
 [_ismbb – rutiny](../../c-runtime-library/ismbb-routines.md)