---
title: __pctype_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
dev_langs:
- C++
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c414ddee654897c88438ec879f9b481073888f4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
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
 [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)