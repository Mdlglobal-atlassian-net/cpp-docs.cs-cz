---
title: Implements::cancastto – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements::CanCastTo
dev_langs:
- C++
helpviewer_keywords:
- CanCastTo method
ms.assetid: a8e85c7d-4dcd-446d-bebc-a97da46ce44a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4fd6e6736c74e1ce895031e17c1d5268eb4ce646
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo – metoda
Získá ukazatele k zadanému rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odkaz na rozhraní ID.  
  
 `ppv`  
 Pokud úspěšné, ukazatel na rozhraní zadán `riid`.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak, který značí chybu, jako je například E_NOINTERFACE HRESULT.  
  
## <a name="remarks"></a>Poznámky  
 Toto je k interní pomocné funkce, který provede operaci QueryInterface.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Implements – struktura](../windows/implements-structure.md)