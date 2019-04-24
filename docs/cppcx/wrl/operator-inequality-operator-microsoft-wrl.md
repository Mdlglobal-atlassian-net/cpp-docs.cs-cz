---
title: operator!= – operátor (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator!=
ms.assetid: 785435da-87a6-4454-9bce-9d288a96dc26
ms.openlocfilehash: 6068a7ddad78e3347f6987b30cc2884dc3f648fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232257"
---
# <a name="operator-operator-microsoftwrl"></a>operator!= – operátor (Microsoft::WRL)

Operátor nerovnosti pro [ComPtr](comptr-class.md) a [comptrref –](comptrref-class.md) objekty.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator!=(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator!=(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator!=(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Levý objekt.

*b*<br/>
Pravý objekt.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud objekty nejsou stejné; jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)