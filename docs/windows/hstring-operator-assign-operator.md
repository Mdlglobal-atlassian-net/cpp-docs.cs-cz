---
title: HString::Operator = – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6fd1082beb6d84c5dded008e20683f7292cbc1e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873869"
---
# <a name="hstringoperator-operator"></a>HString::Operator= – operátor
Hodnota jiného objektu HString přesune na aktuální objekt HString.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HString& operator=(HString&& other) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Existující objekt HString.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota existující `other` objektu se zkopíruje do aktuální objekt HString a potom `other` zničena objektu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)