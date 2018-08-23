---
title: ComPtrRef::operator! = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::operator!=
dev_langs:
- C++
ms.assetid: ab3093cc-6fbd-4039-890a-6df1cde992b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 97a0f98044e18ec6eff1f1b99e9c9178b711e040
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596020"
---
# <a name="comptrrefoperator-operator"></a>ComPtrRef::operator!= – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)  
);

bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);

bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);

bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*a*  
Odkaz na **comptrref –** objektu.

*b*  
Odkaz na jiný **comptrref –** objekt nebo ukazatel na anonymní objekt (`void*`).

## <a name="return-value"></a>Návratová hodnota

První operátor výnosy **true** Pokud objekt *a* není roven objektu *b*; v opačném případě **false**.

Druhý a třetí operátory yield **true** Pokud objekt *a* není roven **nullptr**; v opačném případě **false**.

Čtvrtý a pátý operátory yield **true** Pokud objekt *a* není roven objektu *b*; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Určuje, zda dva **comptrref –** objekty nejsou stejné.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)  
[ComPtrRef – třída](../windows/comptrref-class.md)