---
title: Weakreference::setunknown – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs:
- C++
helpviewer_keywords:
- SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 28b25645b21d3101e2f2b2004f02f29482320808
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891012"
---
# <a name="weakreferencesetunknown-method"></a>WeakReference::SetUnknown – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void SetUnknown(  
   _In_ IUnknown* unk  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `unk`  
 Ukazatel `IUnknown` rozhraní objektu.  
  
## <a name="remarks"></a>Poznámky  
 Nastaví odkaz na silné aktuálního `WeakReference` objekt, který má ukazatel zadaný rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také
[WeakReference – třída](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)