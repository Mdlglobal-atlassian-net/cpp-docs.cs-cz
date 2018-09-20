---
title: Asyncbase::ErrorCode – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ErrorCode
dev_langs:
- C++
helpviewer_keywords:
- ErrorCode method
ms.assetid: 3f5f0f69-d60a-4a67-8cc6-a55fdc89a192
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8da9da0ffbfb8291082f7f600ca72bf1937c3bfc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435542"
---
# <a name="asyncbaseerrorcode-method"></a>AsyncBase::ErrorCode – metoda

Získá kód chyby pro aktuální asynchronní operaci.

## <a name="syntax"></a>Syntaxe

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parametry

*Chyba*<br/>
Umístění, kde tato operace ukládá aktuální kód chyby.

## <a name="remarks"></a>Poznámky

Tato operace je bezpečná pro vlákno.

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[AsyncBase – třída](../windows/asyncbase-class.md)