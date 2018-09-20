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
ms.openlocfilehash: a6e21f89b5f1beb035b2dd87b2d0ad1d55bc3f8f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418050"
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

*Chyba*<br/>
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