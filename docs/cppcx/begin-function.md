---
title: begin – funkce
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258288"
---
# <a name="begin-function"></a>begin – funkce

Vrátí iterátor odkazující na začátek kolekce, která se využívají v parametru zadané rozhraní.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru šablony.

*v*<br/>
Kolekce vektoru\<T > nebo VectorView\<T > objekty, které přistupují IVector\<T > nebo IVectorView\<T > rozhraní.

*i*<br/>
Kolekce objektů libovolného modulu Windows Runtime, které přistupují IIterable\<T > rozhraní.

### <a name="return-value"></a>Návratová hodnota

Iterátor, který odkazuje na začátku kolekce.

### <a name="remarks"></a>Poznámky

První dvě funkce šablony vrátí iterátory a třetí funkce šablony vrátí vstupní iterátor.

VectorIterator objekt, který je vrácený začít je proxy iterátor, který ukládá prvky typu VectorProxy\<T >. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Windows::Foundation::Collections

## <a name="see-also"></a>Viz také:

[Windows::Foundation::Collections – obor názvů](../cppcx/windows-foundation-collections-namespace-c-cx.md)
