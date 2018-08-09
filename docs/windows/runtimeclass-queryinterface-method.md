---
title: Runtimeclass::QueryInterface – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 8f01f4a1-3fa2-4a8e-88c6-03629236cb9f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d76e2e7041948021cb36e563acef7ca712e73842
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015192"
---
# <a name="runtimeclassqueryinterface-method"></a>RuntimeClass::QueryInterface – metoda
Načte ukazatel na ID zadané rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   QueryInterface  
)  
   (REFIID riid,   
   _Deref_out_ void **ppvObject);  
```  
  
### <a name="parameters"></a>Parametry  
 *riid*  
 Identifikátor rozhraní.  
  
 *ppvObject*  
 Když tento opereation se dokončí, ukazatel na rozhraní určené typem *riid* parametru.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)