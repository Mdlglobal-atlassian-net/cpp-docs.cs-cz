---
title: Comptr::AS – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 2ad6c262-9bdb-4c59-a330-1af8bcd445cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ffb84fd072f4ddd3dc76445c720debef5c364642
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42590432"
---
# <a name="comptras-method"></a>ComPtr::As – metoda

Vrátí **ComPtr** objekt, který představuje rozhraní identifikován parametrem určené šablony.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parametry

*U*  
Rozhraní a nelze je reprezentovat podle parametrů *p*.

*p*  
A **ComPtr** objekt, který představuje rozhraní určené typem parametru *U*. Parametr *p* nesmí odkazovat na aktuální **ComPtr** objektu.

## <a name="remarks"></a>Poznámky

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona se osobní a specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../cpp/auto-cpp.md) klíčovým slovem odvození typu.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)