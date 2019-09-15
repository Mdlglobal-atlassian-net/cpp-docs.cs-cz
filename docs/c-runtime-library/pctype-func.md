---
title: __pctype_func
ms.date: 11/04/2016
api_name:
- __pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: f5dae74dd601df1dc737293a181eca60f5cd23f8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944032"
---
# <a name="__pctype_func"></a>__pctype_func

Načte ukazatel na pole informací o klasifikaci znaků.

## <a name="syntax"></a>Syntaxe

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na pole informací o klasifikaci znaků.

## <a name="remarks"></a>Poznámky

Informace v tabulce klasifikace znaků jsou pouze pro interní použití a jsou používány různými funkcemi, které klasifikují znaky typu `char`. Další informace najdete v `Remarks` části [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__pctype_func|CType. h|

## <a name="see-also"></a>Viz také:

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
