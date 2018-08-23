---
title: HStringReference::Operator&lt; operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee7edbee285df6da752e875ac4d86a74e8f7893d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594138"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; – operátor

Označuje, zda je první parametr je menší než druhý parametr.

## <a name="syntax"></a>Syntaxe

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*lhs*  
První parametr k porovnání. *LHS* může být odkazem na **HStringReference**.

*Zarovnání indirekce RHS*  
Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být odkazem na **HStringReference**.

## <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* parametr je menší než *zarovnání indirekce rhs* parametr; v opačném případě **false**.

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="see-also"></a>Viz také

[HStringReference – třída](../windows/hstringreference-class.md)