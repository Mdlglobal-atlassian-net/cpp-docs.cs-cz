---
title: Hstring::hstring – konstruktor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3188e137d3a39fb26ca4151f72073306038e46f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="hstringhstring-constructor"></a>HString::HString – konstruktor
Inicializuje novou instanci třídy HString.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString(HSTRING hstr = nullptr) throw();  
HString(HString&& other) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `hstr`  
 Popisovač HSTRING.  
  
 `other`  
 Existující objekt HString.  
  
## <a name="remarks"></a>Poznámky  
 První konstruktor inicializuje nový objekt HString, který je prázdný.  
  
 Druhý konstruktor inicializuje nový objekt HString na hodnotu existující `other` parametr a pak zničí `other` parametr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)