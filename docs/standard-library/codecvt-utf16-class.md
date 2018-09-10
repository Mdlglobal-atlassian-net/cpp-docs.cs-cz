---
title: codecvt_utf16 – | Dokumentace Microsoftu
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
ms.openlocfilehash: 9614303e62d3d1ca374eecca8c04cc30a7f94106
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109794"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Představuje [národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která převede mezi široké znaky zakódován jako UCS-2 nebo UCS-4 a kódováním UTF-16LE nebo UTF-16BE datový proud bajtů.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem*<br/>
Typ elementu širokého znaku.
*Maxcode*<br/>
Maximální počet znaků pro omezující vlastnost národního prostředí.
*Režim*<br/>
Informace o konfiguraci pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Této třídy šablony převede mezi široké znaky zakódován jako UCS-2 nebo UCS-4 a datový proud bajtů kódováním UTF-16LE, pokud režim & little_endian nebo UTF-16BE jinak.

Bajtový proud by měly být zapsány do binárního souboru; může být poškozený, pokud zapsána do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt – > Namespace: std