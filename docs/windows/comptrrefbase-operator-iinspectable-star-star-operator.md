---
title: "ComPtrRefBase::operator operátor IInspectable ** | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs:
- C++
helpviewer_keywords:
- operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d83580537a81b1c75f44e32e6aa43b2b014c8373
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="comptrrefbaseoperator-iinspectable-operator"></a>ComPtrRefBase::operator Operátor IInspectable**

Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
operator IInspectable**() const;
```

## <a name="remarks"></a>Poznámky

Vrhá aktuální [ptr_ –](../windows/comptrrefbase-ptr-data-member.md) data člena ukazatel k ukazatele k rozhraní IInspectable.

Pokud aktuální ComPtrRefBase není odvozena od IInspectable, jsou vydávány k chybě.

Toto přetypování je k dispozici pouze v případě **&#95; &#95; WRL_CLASSIC_COM &#95; &#95;**  je definována.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ComPtrRefBase – třída](../windows/comptrrefbase-class.md)   
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)