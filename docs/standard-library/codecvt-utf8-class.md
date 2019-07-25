---
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: dcbb34c300d7c15f89c4a882275be0efd68359dc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458706"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Představuje omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která převádí mezi znaky zakódovanými jako UCS-2 nebo UCS-4 a datový proud bajtů KÓDOVANÝ jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ elementu s velkým znakem.

*Maxcode*\
Maximální počet znaků pro omezující vlastnost národního prostředí.

*Mode*\
Konfigurační informace pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Bajtový datový proud lze zapsat do binárního souboru nebo do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt >

Obor názvů: std
