---
title: HStringReference::Operator! = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
dev_langs:
- C++
ms.assetid: 01ab6691-1fc7-4feb-85f0-fe795593a160
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 996ead81a72fb3cc58544576059a8347972e2a6b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429054"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator!= – operátor

Určuje, zda dva parametry nerovnají.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr k porovnání. *LHS* může být **HStringReference** objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být **HStringReference** objektu nebo popisovače HSTRING.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry nejsou stejné; jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HStringReference – třída](../windows/hstringreference-class.md)