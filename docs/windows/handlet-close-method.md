---
title: Handlet::Close – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::Close
dev_langs:
- C++
helpviewer_keywords:
- Close method
ms.assetid: 1b9d597c-abcf-4028-a068-0344560009f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab919b3aeba45462a15900429493225f00909d5a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602451"
---
# <a name="handletclose-method"></a>HandleT::Close – metoda

Zavře aktuální **HandleT** objektu.

## <a name="syntax"></a>Syntaxe

```cpp
void Close();
```

## <a name="remarks"></a>Poznámky

Popisovač, které je základem aktuální **handlet –** je zavřená a **HandleT** je nastavena na neplatný stav.

Pokud je popisovač nezavírá správně, je vyvolána výjimka ve volajícím vlákně.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HandleT – třída](../windows/handlet-class.md)