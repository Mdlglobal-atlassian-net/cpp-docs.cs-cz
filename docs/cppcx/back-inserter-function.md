---
title: back_inserter – funkce
ms.date: 12/30/2016
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
ms.openlocfilehash: 82df6b06389fa9f1c3ab83fa7b1da3bab092c68d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209439"
---
# <a name="backinserter-function"></a>back_inserter – funkce

Vrátí iterátor, který slouží k vložení prvků na konci zadané kolekci.

## <a name="syntax"></a>Syntaxe

```

template <typename T>
Platform::BackInsertIterator<T>
    back_inserter(IVector<T>^ v);

template<typename T>
Platform::BackInsertIterator<T>
   back_inserter(IObservableVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru šablony.

*v*<br/>
Ukazatel rozhraní, která poskytuje přístup ke zdrojové kolekce.

### <a name="return-value"></a>Návratová hodnota

Iterátor.

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Windows::Foundation::Collections

## <a name="see-also"></a>Viz také:

[Windows::Foundation::Collections – obor názvů](../cppcx/windows-foundation-collections-namespace-c-cx.md)
