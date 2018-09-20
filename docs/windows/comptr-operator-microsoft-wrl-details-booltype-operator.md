---
title: ComPtr::operator Microsoft::WRL::Details::BoolType operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: cfba6521-fb30-4fb8-afb2-cfab1cb5e0b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 05e26296646b61997baff880a671958769eb099b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46433397"
---
# <a name="comptroperator-microsoftwrldetailsbooltype-operator"></a>ComPtr::operator Microsoft::WRL::Details::BoolType – operátor

Určuje, zda je či není **ComPtr** spravuje doba života objektu rozhraní.

## <a name="syntax"></a>Syntaxe

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

## <a name="return-value"></a>Návratová hodnota

Pokud je přidruženo toto rozhraní **ComPtr**, adresu [boolstruct::Member –](../windows/boolstruct-member-data-member.md) datový člen; v opačném případě **nullptr**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[ComPtr – třída](../windows/comptr-class.md)<br/>
[ComPtr::Get – metoda](../windows/comptr-get-method.md)