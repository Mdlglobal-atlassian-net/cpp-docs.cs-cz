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
ms.openlocfilehash: 24ca52eccc814b82e5f9bdd6ddac6458fb5992fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607133"
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

*a*  
Odkaz na **ComPtr** objektu.

*b*  
Odkaz na jiný **ComPtr** objektu.

## <a name="return-value"></a>Návratová hodnota

První operátor výnosy **true** Pokud objekt *a* rovná objektu *b*; v opačném případě **false**.

Druhý a třetí operátory yield **true** Pokud objekt *a* rovná **nullptr**; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)  
[ComPtr – třída](../windows/comptr-class.md)