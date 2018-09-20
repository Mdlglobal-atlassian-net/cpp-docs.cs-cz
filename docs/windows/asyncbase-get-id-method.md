---
title: Asyncbase::get_id – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Id
dev_langs:
- C++
helpviewer_keywords:
- get_Id method
ms.assetid: 591d8366-ea76-4deb-9278-9d3bc394a42b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee4e15293d3f1f7b5b364ea22eeea2385cc9e855
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46403874"
---
# <a name="asyncbasegetid-method"></a>AsyncBase::get_Id – metoda

Načte popisovač asynchronní operace.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parametry

*id*<br/>
Umístění, kam se uloží popisovač.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Id`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)