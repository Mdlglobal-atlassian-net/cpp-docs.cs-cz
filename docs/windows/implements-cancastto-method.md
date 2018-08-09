---
title: Implements::cancastto – metoda | Dokumentace Microsoftu
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
ms.openlocfilehash: a73aac6fb36270f0cd04615d9e530b29841850f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40010919"
---
# <a name="implementscancastto-method"></a>Implements::CanCastTo – metoda
Získá ukazatel na rozhraní zadané.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__forceinline HRESULT CanCastTo(  
   REFIID riid,  
   _Deref_out_ void **ppv  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Odkaz na identifikátor rozhraní.  
  
 *ppv*  
 Pokud úspěšná, ukazatel na rozhraní určené *riid*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu, například E_NOINTERFACE.  
  
## <a name="remarks"></a>Poznámky  
 Toto je interní pomocné funkce, který provádí operace QueryInterface.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Implements – struktura](../windows/implements-structure.md)