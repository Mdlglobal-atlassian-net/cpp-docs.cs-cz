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
ms.openlocfilehash: 4ea49833107bf58443bf4a8238229d1d63a86742
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010344"
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