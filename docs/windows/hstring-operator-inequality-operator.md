---
title: HString::Operator! = – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs:
- C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96131bc566271de9d99d1530ffb407c0870c71a7
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604322"
---
# <a name="hstringoperator-operator"></a>HString::Operator!= – operátor

Určuje, zda dva parametry nerovnají.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*lhs*  
První parametr k porovnání. *LHS* může být **HString** nebo `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*  
Druhý parametr k porovnání. *zarovnání indirekce rhs* může být **HString** nebo `HStringReference` objektu nebo popisovače HSTRING.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry nejsou stejné; jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)