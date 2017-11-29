---
title: "ComPtrRefBase::operator operátor IInspectable ** | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
dev_langs: C++
helpviewer_keywords: operator IInspectable** operator
ms.assetid: 06ac1051-606c-449b-a566-cac78ca53762
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0c3b51191c6dd5627bd25a110beb6bff9a9c60f7
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
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
[Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)