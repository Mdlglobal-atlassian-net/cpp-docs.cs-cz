---
title: Criticalsection::criticalsection – konstruktor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::CriticalSection::CriticalSection
dev_langs:
- C++
helpviewer_keywords:
- CriticalSection, constructor
ms.assetid: 930b89be-4d74-46bd-8879-5dd4d15bcbd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b992f4ad781105a8795a7bf95ff8b831ab961275
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400669"
---
# <a name="criticalsectioncriticalsection-constructor"></a>CriticalSection::CriticalSection – konstruktor

Inicializuje objekt synchronizace, který je podobný objektu mutex, ale může využívat pouze vláken v jednom procesu.

## <a name="syntax"></a>Syntaxe

```cpp
explicit CriticalSection(
   ULONG spincount = 0
);
```

### <a name="parameters"></a>Parametry

*spincount*<br/>
Počet typu číselník pro objekt kritický oddíl. Výchozí hodnota je 0.

## <a name="remarks"></a>Poznámky

Další informace o kritických oddílů a spincounts, najdete v článku `InitializeCriticalSectionAndSpinCount` fungovat v **synchronizace** část jejich rozhraní Windows API.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[CriticalSection – třída](../windows/criticalsection-class.md)