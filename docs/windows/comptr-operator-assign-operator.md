---
title: ComPtr::operator = – operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6b221ff75e250830feefbbd2d3db0d8697095c96
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/22/2018
---
# <a name="comptroperator-operator"></a>ComPtr::operator= – operátor
Přiřadí aktuální ComPtr hodnotu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Třída.  
  
 `other`  
 Ukazatelů, reference nebo rvalue odkaz na typ nebo jinou ComPtr.  
  
## <a name="return-value"></a>Návratová hodnota  
 Odkaz na aktuální ComPtr.  
  
## <a name="remarks"></a>Poznámky  
 První verze součásti tento operátor přiřadí aktuální ComPtr prázdnou hodnotu.  
  
 V druhé verze Pokud přiřazení ukazatel rozhraní není stejný jako aktuální ukazatel rozhraní ComPtr druhý ukazatel rozhraní přiřazen aktuální ComPtr.  
  
 Ve třetí verzi přiřazení ukazatel rozhraní je přiřazený k aktuální ComPtr.  
  
 V Čtvrtá verze pokud ukazatel rozhraní přiřazení hodnoty není stejný jako aktuální ukazatel rozhraní ComPtr druhý ukazatel rozhraní přiřazen aktuální ComPtr.  
  
 Je pátá verze kopie operátor; odkaz na ComPtr je přiřazen k aktuální ComPtr.  
  
 Šesté verze je kopie operátor, který používá přesunout sémantiku; deklarátor odkazu na ComPtr pokud přetypování a posléze přiřazeny k aktuální ComPtr je statický libovolného typu.  
  
 Sedmého verze je kopie operátor, který používá přesunout sémantiku; rvalue odkaz na ComPtr typu `U` se statickou přetypovat pak a přiřadí do aktuální ComPtr.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)