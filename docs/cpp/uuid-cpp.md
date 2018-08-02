---
title: UUID (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- uuid_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 93ae3ac7f0d6fff700e1c89aad197d5f03734cf5
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467105"
---
# <a name="uuid-c"></a>uuid (C++)
**Specifické pro Microsoft**  
  
 Kompilátor připojí identifikátor GUID ke třídě nebo struktuře deklarované nebo definované (úplná definice objektu modelu COM pouze) se **uuid** atribut.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 **Uuid** atribut přijímá řetězec jako svůj argument. Tento řetězec pojmenuje identifikátor GUID v normálním formátu registru s nebo bez něj **{}** oddělovače. Příklad:  
  
```cpp 
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Tento atribut lze použít v opětovné deklaraci. To hlavičkám systému poskytnout definici rozhraní umožňuje `IUnknown`a opětovnou deklaraci v jiném souboru hlaviček (například \<comdef.h >) k zadání identifikátoru GUID.  
  
 Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) lze použít k získání konstanty identifikátoru GUID připojeného k uživatelem definovaného typu.  
  
 **Specifické pro END Microsoft**  
  
## <a name="see-also"></a>Viz také:  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)