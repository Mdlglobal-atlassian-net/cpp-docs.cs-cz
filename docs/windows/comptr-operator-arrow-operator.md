---
title: ComPtr::operator -&gt; operátor | Microsoft Docs
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
ms.openlocfilehash: 3cb3571207f328ad044ffd3f2f9b83bcebc7677e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator -&gt; – operátor
Načte ukazatel na typ určený parametrem aktuální šablony.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na v typu zadaném pomocí názvu typu aktuální šablony.  
  
## <a name="remarks"></a>Poznámky  
 Tato pomocná funkce odebere nárokům na způsobil pomocí STDMETHOD – makro. Díky této funkci IUnknown typy privátní místo virtuální.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)