---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: a84ca6da22825ca3fa7ab43e43a574fb05caa1a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689828"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Představuje omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která je převedena mezi velké znaky kódované jako UCS-2 nebo UCS-4 a datový proud bajtů KÓDOVANÝ jako UTF-16LE nebo UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parametry

*Elem* \
Typ elementu s velkým znakem.

*Maxcode* \
Maximální počet znaků pro omezující vlastnost národního prostředí.

@No__t_1 *režimu*
Konfigurační informace pro omezující vlastnost národního prostředí.

## <a name="remarks"></a>Poznámky

Tato šablona třídy převádí mezi znaky s kódováním UCS-2 nebo UCS-4 a datový proud bajtů kódovaný jako UTF-16LE, pokud mode & little_endian nebo UTF-16BE v opačném případě.

Datový proud bajtů by měl být zapsán do binárního souboru; může být poškozený, pokud je zapsán do textového souboru.

## <a name="requirements"></a>Požadavky

Záhlaví: \<codecvt >

Obor názvů: std