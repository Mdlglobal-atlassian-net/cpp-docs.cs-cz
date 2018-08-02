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
ms.openlocfilehash: 19e04f5415f9f7a736371c888dff7559df6c6c66
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39462333"
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

Toto přetypování je k dispozici pouze tehdy, pokud **&#95; &#95;WRL_CLASSIC_COM&#95; &#95;** je definována.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také
[Comptrrefbase – třída](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)