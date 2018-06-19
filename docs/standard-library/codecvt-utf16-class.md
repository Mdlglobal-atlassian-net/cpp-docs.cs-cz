---
title: codecvt_utf16 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf16
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93113e64e9b6a72f40557d063f83724c5ff8da62
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33841063"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Představuje [národního prostředí](../standard-library/locale-class.md) omezující vlastnosti, který převádí mezi široké znaky kódovaná jako UCS-2 nebo UCS 4 a datového proudu bajtů kódování UTF-16LE nebo UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

`Elem` Typ elementu široká charakterová.
`Maxcode` Maximální počet znaků pro omezující vlastnost národního prostředí.
`Mode` Informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Tato třída šablony převede mezi široké znaky kódovaná jako UCS-2 nebo UCS 4 a datového proudu bajtů kódovaná jako znakové sady UTF-16LE, pokud režim & little_endian nebo UTF-16BE jinak.

Datový proud bajtů by měly být zapsány do binárního souboru; může být poškozená, pokud zapsána do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt – > Namespace: – std