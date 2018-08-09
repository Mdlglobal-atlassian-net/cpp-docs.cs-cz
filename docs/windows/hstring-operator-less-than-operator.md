---
title: HString::Operator&lt; operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1bdc6d54a6c9b60036d7434edec960715db304e2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40017679"
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; – operátor
Označuje, zda je první parametr je menší než druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *lhs*  
 První parametr k porovnání. *LHS* může být odkazem na **HString**.  
  
 *Zarovnání indirekce RHS*  
 Druhý parametr k porovnání. *Zarovnání indirekce RHS* může být odkazem na **HString**.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud *lhs* parametr je menší než *zarovnání indirekce rhs* parametr; v opačném případě **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)