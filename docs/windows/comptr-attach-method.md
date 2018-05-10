---
title: Comptr::Attach – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::Attach
dev_langs:
- C++
helpviewer_keywords:
- Attach method
ms.assetid: 5b911f2d-9830-4dc7-b9e3-527abd55d2c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 590a50fbaca22b088af39f31e2e6349a3ebc18dd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="comptrattach-method"></a>ComPtr::Attach – metoda
Přidruží tento ComPtr určeného parametrem aktuální typ šablony typu rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Attach(  
   _In_opt_ InterfaceType* other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `other`  
 Typ rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)