---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 67447823b0322e647784cdbe0f3f7228e1c5fb34
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919237"
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

Informace v tabulce klasifikace znaků jsou pouze pro interní použití a jsou používány různými funkcemi, které klasifikují znaky typu `char`. Další informace najdete v `Remarks` části [_pctype, _pwctype, _wctype _mbctype _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

Ve výchozím nastavení je globální stav této funkce vymezen na aplikaci. Pokud ho chcete změnit, přečtěte si téma [globální stav v CRT](global-state.md).

## <a name="requirements"></a>Požadavky

|Rutina|Požadovaný hlavičkový soubor|
|-------------|---------------------|
|__pctype_func|CType. h|

## <a name="see-also"></a>Viz také

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
