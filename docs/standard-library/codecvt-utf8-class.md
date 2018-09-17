---
title: codecvt_utf8 – | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5dce174d9c6edca45946ba8ad60165e62e3591fd
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718481"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Představuje [národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která převede mezi široké znaky zakódován jako UCS-2 nebo UCS-4 a datový proud bajtů kódováním UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu širokého znaku.

*Maxcode*<br/>
Maximální počet znaků pro omezující vlastnost národního prostředí.

*Režim*<br/>
Informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Bajtový proud je možné zapisovat na binární soubor nebo textový soubor.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt – > \

Namespace: std
