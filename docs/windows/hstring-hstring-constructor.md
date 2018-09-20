---
title: Hstring::hstring – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
dev_langs:
- C++
ms.assetid: 6da12785-ed01-4720-a004-667db60298f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 59ec7c1635b825cc300e28e5c02e2a3864a6c123
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442250"
---
# <a name="hstringhstring-constructor"></a>HString::HString – konstruktor

Inicializuje novou instanci třídy **HString** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>Parametry

*HSTR*<br/>
Popisovač HSTRING.

*Ostatní*<br/>
Existující **HString** objektu.

## <a name="remarks"></a>Poznámky

První konstruktor inicializuje novou **HString** objekt, který je prázdný.

Druhý konstruktor inicializuje novou **HString** objektu na hodnotu stávající *jiných* parametr a potom zničí *jiných* parametru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)