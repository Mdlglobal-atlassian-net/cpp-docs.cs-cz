---
title: ComPtr::operator -&gt; operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator->
dev_langs:
- C++
helpviewer_keywords:
- operator-> operator
ms.assetid: 7b7faefd-d1e4-4f31-a77d-17a42e0d6b6a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 417fd11017f9f70ee8cc247898e23741488ae5e7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599985"
---
# <a name="comptroperator-gt-operator"></a>ComPtr::operator -&gt; – operátor

Načte ukazatel na typ určený v parametru aktuální šablony.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na typ určený aktuální typ název šablony.

## <a name="remarks"></a>Poznámky

Tato pomocná funkce odebere zbytečnou režii způsobena použitím STDMETHOD – makro. Díky této funkci `IUnknown` typy **privátní** místo **virtuální**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)