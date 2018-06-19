---
title: ComPtr::operator&amp; operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0bfe8cf9091d888c33420f53f584ca5509d80527
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872403"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; – operátor
Verze rozhraní přidružený k tomuto `ComPtr` objekt a potom načte adresu `ComPtr` objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
Details::ComPtrRef<WeakRef> operator&()  
  
const Details::ComPtrRef<const WeakRef> operator&() const  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Slabé odkazy na aktuální `ComPtr`.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se liší od [comptr::getaddressof –](../windows/comptr-getaddressof-method.md) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použití `ComPtr::GetAddressOf` když vyžadovat adresy ukazatele rozhraní, ale nechcete, aby k uvolnění tohoto rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ComPtr – třída](../windows/comptr-class.md)