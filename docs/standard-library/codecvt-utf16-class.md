---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: ca66a3273567a8d30a982211a6e977c129b00f5f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459714"
---
# <a name="codecvtutf16"></a>codecvt_utf16

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

*Mode*\
Konfigurační informace pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Tato třída šablony převádí mezi znaky s kódováním UCS-2 nebo UCS-4 a datový proud bajtů kódovaný jako UTF-16LE, pokud mode & little_endian nebo UTF-16BE v opačném případě.

Datový proud bajtů by měl být zapsán do binárního souboru; může být poškozený, pokud je zapsán do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt >

Obor názvů: std