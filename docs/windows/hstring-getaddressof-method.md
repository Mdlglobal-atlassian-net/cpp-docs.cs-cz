---
title: Hstring::getaddressof – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613362"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf – metoda

Načte ukazatel na podkladové popisovač HSTRING.

## <a name="syntax"></a>Syntaxe

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladové popisovač HSTRING.

## <a name="remarks"></a>Poznámky

Po provedení této operace je zničen řetězcovou hodnotu podkladového popisovače HSTRING.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)