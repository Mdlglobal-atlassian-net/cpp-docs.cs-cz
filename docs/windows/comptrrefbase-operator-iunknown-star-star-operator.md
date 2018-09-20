---
title: ComPtrRefBase::operator IUnknown ** – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
dev_langs:
- C++
helpviewer_keywords:
- operator IUnknown** operator
ms.assetid: c2950abf-a7aa-480a-ba41-615703e7f931
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 839b0220497db7ff0355ea7ed3ab923126e3175e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420930"
---
# <a name="comptrrefbaseoperator-iunknown-operator"></a>ComPtrRefBase::operator IUnknown** – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
operator IUnknown**() const;
```

## <a name="remarks"></a>Poznámky

Přetypování aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) na ukazatel na ukazatel – datový člen `IUnknown` rozhraní.

Je vygenerován chybu, pokud aktuální **comptrrefbase –** není odvozen od `IUnknown`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ComPtrRefBase – třída](../windows/comptrrefbase-class.md)<br/>
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)