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
ms.openlocfilehash: 80af8f463d6cd1af631c6cb37c0239e7a9e85c3f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42595882"
---
# <a name="hstringhstring-constructor"></a>HString::HString – konstruktor

Inicializuje novou instanci třídy **HString** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

#### <a name="parameters"></a>Parametry

*HSTR*  
Popisovač HSTRING.

*Ostatní*  
Existující **HString** objektu.

## <a name="remarks"></a>Poznámky

První konstruktor inicializuje novou **HString** objekt, který je prázdný.

Druhý konstruktor inicializuje novou **HString** objektu na hodnotu stávající *jiných* parametr a potom zničí *jiných* parametru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)