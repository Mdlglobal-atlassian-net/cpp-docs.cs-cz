---
title: ComPtr::operator == – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator==
dev_langs:
- C++
ms.assetid: 6a26e936-29d4-4b7d-b44a-7c575ad07509
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2e0fd86cb8a9c9fa86da0a1781f49fe57c5ce6d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394431"
---
# <a name="comptroperator-operator"></a>ComPtr::operator== – operátor

Určuje, zda dva **ComPtr** objekty rovnají.

## <a name="syntax"></a>Syntaxe

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)  
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Odkaz na **ComPtr** objektu.

*b*<br/>
Odkaz na jiný **ComPtr** objektu.

## <a name="return-value"></a>Návratová hodnota

První operátor výnosy **true** Pokud objekt *a* rovná objektu *b*; v opačném případě **false**.

Druhý a třetí operátory yield **true** Pokud objekt *a* rovná **nullptr**; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)<br/>
[ComPtr – třída](../windows/comptr-class.md)