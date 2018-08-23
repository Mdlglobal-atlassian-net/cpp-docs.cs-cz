---
title: ComPtr::operator&amp; operátor | Dokumentace Microsoftu
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
ms.openlocfilehash: f513ac83e0ee83109f42cf87b80b4fcc4960db1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598600"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; – operátor

Uvolní rozhraní přidružené k tomuto **ComPtr** objekt a potom načte adresu **ComPtr** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

## <a name="return-value"></a>Návratová hodnota

Slabý odkaz na aktuální **ComPtr**.

## <a name="remarks"></a>Poznámky

Tato metoda se liší od [comptr::getaddressof –](../windows/comptr-getaddressof-method.md) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použití `ComPtr::GetAddressOf` když vyžadovat adresy ukazatel rozhraní, ale nechcete, aby k uvolnění rozhraní.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)