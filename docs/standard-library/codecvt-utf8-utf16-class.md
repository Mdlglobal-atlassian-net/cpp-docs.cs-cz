---
title: codecvt_utf8_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::cvt_utf8_utf16
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
ms.openlocfilehash: 42c9c8643edc795748c1f12c5180471f281c4142
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405256"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Představuje [národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která převede mezi široké znaky s kódováním UTF-16 a datový proud bajtů kódováním UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu širokého znaku.

*Maxcode*<br/>
Maximální počet znaků pro omezující vlastnost národního prostředí.

*Mode*<br/>
Informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Bajtový proud je možné zapisovat na binární soubor nebo textový soubor.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt – >

Namespace: std
