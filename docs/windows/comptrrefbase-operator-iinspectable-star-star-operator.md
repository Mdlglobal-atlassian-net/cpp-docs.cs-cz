---
title: ComPtrRefBase::operator IInspectable ** – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4683305b9f7f396168bd9404f6f2501502db3d01
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645019"
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator IInspectable\* \* – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Poznámky

Přetypování aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) na ukazatel na ukazatel – datový člen `IInspectable` rozhraní.

Je vygenerován chybu, pokud aktuální **comptrrefbase –** není odvozen od `IInspectable`.

Toto přetypování je k dispozici pouze tehdy, pokud `__WRL_CLASSIC_COM__` je definována.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také
[Comptrrefbase – třída](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)