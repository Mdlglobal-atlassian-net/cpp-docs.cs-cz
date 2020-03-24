---
title: operator== – operátor (Microsoft::WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::operator==
ms.assetid: 94f383a5-17a9-40c7-9d9c-778acdc54b27
ms.openlocfilehash: f9a3ea9e33adc8a26f34324a8660c835f08b3007
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213678"
---
# <a name="operator-operator-microsoftwrl"></a>operator== – operátor (Microsoft::WRL)

Operátor rovnosti pro objekty [ComPtr](comptr-class.md) a [ComPtrRef](comptrref-class.md)

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);
WRL_NOTHROW bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   const Details::ComPtrRef<ComPtr<U>>& b
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   decltype(__nullptr)
);
WRL_NOTHROW bool operator==(
   decltype(__nullptr),
   const Details::ComPtrRef<ComPtr<T>>& a
);
WRL_NOTHROW bool operator==(
   const Details::ComPtrRef<ComPtr<T>>& a,
   void* b
);
WRL_NOTHROW bool operator==(
   void* b,
   const Details::ComPtrRef<ComPtr<T>>& a
);
```

### <a name="parameters"></a>Parametry

*určitého*<br/>
Levý objekt

*b*<br/>
Pravý objekt.

## <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou objekty stejné; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)
