---
title: ComPtr::operator -&gt; operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff18dee2b8d951ab9233e92478eb967e4a02eb9
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464295"
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator -&gt; – operátor
Načte ukazatel na typ určený v parametru aktuální šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na typ určený aktuální typ název šablony.  
  
## <a name="remarks"></a>Poznámky  
 Tato pomocná funkce odebere zbytečnou režii způsobena použitím STDMETHOD – makro. Díky této funkci `IUnknown` typy **privátní** místo **virtuální**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)