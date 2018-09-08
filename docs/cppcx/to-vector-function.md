---
title: to_vector – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a3dcccc332a5d768a614414838003e1400f3c6a6
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44107624"
---
# <a name="tovector-function"></a>to_vector – funkce

Vrátí `std::vector` jehož hodnota je stejná jako základní zadaný parametr IVector nebo IVectorView kolekce.

## <a name="syntax"></a>Syntaxe

```
template <typename T>
inline ::std::vector<T> to_vector(IVector<T>^ v);

template <typename T>
inline ::std::vector<T> to_vector(IVectorView<T>^ v);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ parametru šablony.

*v*<br/>
IVector nebo IVectorView rozhraní, které poskytuje přístup k základní objekt vektoru nebo VectorView.

### <a name="return-value"></a>Návratová hodnota

### <a name="requirements"></a>Požadavky

**Záhlaví:** collection.h

**Namespace:** Windows::Foundation:: Collections –

## <a name="see-also"></a>Viz také

[Windows::Foundation:: Collections – Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)