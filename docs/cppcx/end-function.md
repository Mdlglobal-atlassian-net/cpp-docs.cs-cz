---
title: end – funkce
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::end
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
ms.openlocfilehash: c46c601be2b2ed78cf79641a7fcf5324e615a771
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375805"
---
# <a name="end-function"></a>end – funkce

Vrátí iterátor odkazující za koncem kolekce, která se využívají v parametru zadané rozhraní.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru šablony.

*v*<br/>
Kolekce vektoru\<T > nebo VectorView\<T > objekty, které přistupují IVector\<T >, nebo IVectorView\<T > rozhraní.

*i*<br/>
Kolekce arbitraty modulu Windows Runtime objektů, které přistupují IIterable\<T > rozhraní.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který ukazuje za konec kolekce.

### <a name="remarks"></a>Poznámky

První dvě funkce šablony vrátí iterátory a třetí funkce šablony vrátí vstupní iterátor.

[Platform::Collections:: vectorviewiterator –](../cppcx/platform-collections-vectorviewiterator-class.md) objekt, který je vrácený `end` je proxy iterátor, který ukládá prvky typu `VectorProxy<T>`. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Windows::Foundation::Collections

## <a name="see-also"></a>Viz také:

[Windows::Foundation::Collections – obor názvů](../cppcx/windows-foundation-collections-namespace-c-cx.md)
