---
title: codecvt_utf8_utf16 – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::cvt_utf8_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8_utf16 class
ms.assetid: 4c12c881-5dba-4e39-b338-0b9caff5af29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 545fda08a027b1610f82d17c89ae98241ee5502b
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38958127"
---
# <a name="codecvtutf8utf16"></a>codecvt_utf8_utf16

Představuje [národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která převede mezi široké znaky s kódováním UTF-16 a datový proud bajtů kódováním UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8_utf16 : public _STD codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem* typ elementu širokého znaku.
*Maxcode* maximální počet znaků pro omezující vlastnost národního prostředí.
*Režim* informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Bajtový proud je možné zapisovat na binární soubor nebo textový soubor.

## <a name="requirements"></a>Požadavky

Záhlaví: <codecvt> Namespace: std
