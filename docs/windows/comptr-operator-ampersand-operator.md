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
ms.openlocfilehash: 2b464a77fedf0d996210040b744faea0ee7372ef
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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