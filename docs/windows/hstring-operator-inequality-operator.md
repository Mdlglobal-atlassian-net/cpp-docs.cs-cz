---
title: "HString::Operator! = – operátor | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
dev_langs: C++
ms.assetid: dcdd2aca-e7d6-4bf1-b2de-03efbb430a93
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5aab0784b2a099a104fee696148fb9d7ec0c5ac9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hstringoperator-operator"></a>HString::Operator!= – operátor
Určuje, zda dva parametry nejsou stejné.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 První parametr k porovnání. `lhs`může být objekt HString nebo HStringReference nebo popisovač HSTRING.  
  
 `rhs`  
 Druhý parametr k porovnání.`rhs` může být objekt HString nebo HStringReference nebo popisovač HSTRING.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud `lhs` a `rhs` parametry nejsou stejné, jinak hodnota `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)