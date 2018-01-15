---
title: "ComPtr::operator&amp; operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator&
dev_langs: C++
helpviewer_keywords: operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cc5234f10a16141fd91193d634f0d306886aff71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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