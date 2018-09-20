---
title: Asyncbase::get_status – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::get_Status
dev_langs:
- C++
helpviewer_keywords:
- get_Status method
ms.assetid: 9823ecb9-212e-471d-b76f-7b8f21208905
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c1bb13773736104354d6276fef0a731aa72f22d2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431239"
---
# <a name="asyncbasegetstatus-method"></a>AsyncBase::get_Status – metoda

Načte hodnotu označující stav asynchronní operace.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parametry

*Stav*<br/>
Umístění, kde má být uložen stav. Další informace najdete v tématu `Windows::Foundation::AsyncStatus` výčtu.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="remarks"></a>Poznámky

Tato metoda implementuje `IAsyncInfo::get_Status`.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)