---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 73177985727f4da5cf3ca4eb9e3cc3fb5976f76d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215277"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Představuje omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která je převedena mezi velké znaky kódované jako UCS-2 nebo UCS-4 a datový proud bajtů KÓDOVANÝ jako UTF-16LE nebo UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*\
Typ elementu s velkým znakem.

*Maxcode*\
Maximální počet znaků pro omezující vlastnost národního prostředí.

\ *režimu*
Konfigurační informace pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Tato šablona třídy převádí mezi znaky, které jsou zakódovány jako UCS-2 nebo UCS-4 a datový proud bajtů kódovaný jako UTF-16LE, pokud je v režimu & little_endian nebo UTF-16BE.

Datový proud bajtů by měl být zapsán do binárního souboru; může být poškozený, pokud je zapsán do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt >

Obor názvů: std
