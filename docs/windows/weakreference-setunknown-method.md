---
title: "Weakreference::setunknown – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::WeakReference::SetUnknown
dev_langs: C++
helpviewer_keywords: SetUnknown method
ms.assetid: 5dddb9e3-a7c1-4195-8166-97c5ab6e972f
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 82a556ddc855c2ab9793f74fa091c464e094cb80
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)