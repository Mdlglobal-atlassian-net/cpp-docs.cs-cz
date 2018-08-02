---
title: Comptr::getaddressof – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 972a41d0-c2ef-4ae3-b2cd-77cc45156ac9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e11cd204c2c89c7fca9a824450d6136eb65520db
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461181"
---
# <a name="comptrgetaddressof-method"></a>ComPtr::GetAddressOf – metoda
Načte adresu [ptr_ –](../windows/comptr-ptr-data-member.md) datový člen, který obsahuje ukazatel na rozhraní představovaného tímto rozhraním **ComPtr**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
T* const* GetAddressOf() const;  
T** GetAddressOf();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Adresa proměnné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)