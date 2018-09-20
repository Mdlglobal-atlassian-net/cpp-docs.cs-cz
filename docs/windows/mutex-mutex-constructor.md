---
title: Mutex::mutex – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7436aeb470804bd47dcc647ff0fe9a13faaae95
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444278"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex – konstruktor

Inicializuje novou instanci třídy **Mutex** třídy.

## <a name="syntax"></a>Syntaxe

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Popisovač nebo odkaz rvalue na popisovač, na **Mutex** objektu.

## <a name="remarks"></a>Poznámky

První konstruktor inicializuje **Mutex** objekt ze zadaného popisovače. Druhý konstruktor inicializuje **Mutex** objekt Zadaný popisovač a pak přesune vlastnictví mutex do aktuální **Mutex** objektu.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[Mutex – třída](../windows/mutex-class1.md)