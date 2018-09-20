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
ms.openlocfilehash: b5446fb6fa0722018e4ab7734019e677b6acec7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435204"
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

*lhs*<br/>
První parametr k porovnání. *LHS* může být **HString** nebo `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání. *zarovnání indirekce rhs* může být **HString** nebo `HStringReference` objektu nebo popisovače HSTRING.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry nejsou stejné; jinak **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HString – třída](../windows/hstring-class.md)