---
title: Asyncbase::putoncomplete – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b37b11f409e46496dc90389b16cffda848389ba
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46423221"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete – metoda

Nastaví adresu obslužné rutiny události dokončení se zadanou hodnotou.

## <a name="syntax"></a>Syntaxe

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parametry

*completeHandler*<br/>
Adresy, ke kterému je nastavena obslužná rutina události dokončení.

## <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě E_ILLEGAL_METHOD_CALL.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)