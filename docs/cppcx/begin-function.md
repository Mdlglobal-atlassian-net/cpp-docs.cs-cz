---
title: begin – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad73daba0bce57a19c512a53747cf8ac804e929d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101752"
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

VectorIterator objekt, který je vrácený začít je proxy iterátor, který ukládá prvky typu VectorProxy\<T >. Objekt proxy je však téměř nikdy viditelné pro uživatelský kód. Další informace najdete v tématu [kolekce (C + +/ CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Windows::Foundation:: Collections –

## <a name="see-also"></a>Viz také

[Windows::Foundation:: Collections – Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)