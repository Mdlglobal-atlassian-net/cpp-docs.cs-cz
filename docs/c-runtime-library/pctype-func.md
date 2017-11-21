---
title: __pctype_func | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords: __pctype_func
dev_langs: C++
helpviewer_keywords: __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ae2c5f53c10083deb281a88a5f398712722700b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="pctypefunc"></a>__pctype_func
Načte ukazatel na pole znaků klasifikace informace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
const unsigned short *__pctype_func(  
   )  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na pole znaků klasifikace informace.  
  
## <a name="remarks"></a>Poznámky  
 Informace v tabulce klasifikace znak je pouze pro interní použití a používají různé funkce, které klasifikovat znaky typu `char`. Další informace najdete v tématu `Remarks` části [_pctype –, _pwctype –, _wctype –, _mbctype –, _mbcasemap –](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).  
  
## <a name="requirements"></a>Požadavky  
  
|Rutina|Požadovaný hlavičkový soubor|  
|-------------|---------------------|  
|__pctype_func|ctype.h|  
  
## <a name="see-also"></a>Viz také  
 [_pctype –, _pwctype –, _wctype –, _mbctype –, _mbcasemap –](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)