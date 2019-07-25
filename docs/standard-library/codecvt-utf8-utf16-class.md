---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 879ebe6a75d76a84ef4250b95c41e02eccba5517
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458648"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Představuje omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která je převedena mezi velké znaky kódované jako UTF-16 a datový proud bajtů KÓDOVANÝ jako UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
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
