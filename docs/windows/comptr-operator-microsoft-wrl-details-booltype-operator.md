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
ms.openlocfilehash: 135c6d851be5de8f2eb976baf015f2ef449600c0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595970"
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

[ComPtr – třída](../windows/comptr-class.md)  
[ComPtr::Get – metoda](../windows/comptr-get-method.md)