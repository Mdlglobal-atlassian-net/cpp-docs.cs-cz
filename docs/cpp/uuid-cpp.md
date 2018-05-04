---
title: UUID (C++) | Microsoft Docs
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
ms.openlocfilehash: b143def4d758307c6ce6737281bdca1097aaa8c5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="uuid-c"></a>uuid (C++)
**Konkrétní Microsoft**  
  
 Kompilátor připojí identifikátor GUID ke třídě nebo struktuře deklarované nebo definované (pouze úplné definice objektu modelu COM) s atributem `uuid`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
__declspec( uuid("ComObjectGUID") ) declarator  
```  
  
## <a name="remarks"></a>Poznámky  
 Atribut `uuid` přijímá řetězec jako argument. Tento řetězec názvy identifikátor GUID ve formátu normální registru bez ohledu **{}** oddělovače. Příklad:  
  
```  
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;  
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;  
```  
  
 Tento atribut lze použít v opětovné deklaraci. To umožňuje systému hlavičky k poskytování definic rozhraní, jako **IUnknown**a opětovná deklarace v některé jiné záhlaví (například \<comdef.h >) k poskytování identifikátor GUID.  
  
 Klíčové slovo [__uuidof –](../cpp/uuidof-operator.md) lze použít k načtení konstanta GUID připojené k uživatelem definovaného typu.  
  
 **Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [__declspec](../cpp/declspec.md)   
 [Klíčová slova](../cpp/keywords-cpp.md)