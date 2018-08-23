---
title: Asyncbase::trytransitiontoerror – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
dev_langs:
- C++
helpviewer_keywords:
- TryTransitionToError method
ms.assetid: f6d11c25-1ce3-43f9-af1c-97c4dc0f6f0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1244b87410a09996d946408ff77dbb552b339c85
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591151"
---
# <a name="asyncbasetrytransitiontoerror-method"></a>AsyncBase::TryTransitionToError – metoda

Určuje, zda kód zadanou chybovou můžete upravit stavu došlo k vnitřní chybě.

## <a name="syntax"></a>Syntaxe

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parametry

*Chyba*  
Chyba HRESULT.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud státu došlo k vnitřní chybě byla změněné; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Tato operace změní chybový stav, pouze v případě, že chybový stav je již nastavena na hodnotu S_OK. Tato operace nemá žádný vliv, pokud chybový stav je již chyba, zrušena, Dokončeno nebo Uzavřeno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)