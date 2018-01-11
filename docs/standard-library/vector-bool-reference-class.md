---
title: "vektor&lt;bool&gt;:: referenční třídy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vector/vector<bool>::reference
dev_langs: C++
helpviewer_keywords: vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5ebca8cefef2aa53d2726d734932363d54426247
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="vectorltboolgtreference-class"></a>vektor&lt;bool&gt;:: odkazovat – třída
`vector<bool>::reference` Třídy je třída proxy poskytované [vektoru\<bool > třída](../standard-library/vector-bool-class.md) k simulaci `bool&`.  
  
## <a name="remarks"></a>Poznámky  
 Simulovaný odkaz je vyžadován, protože jazyk C++ nativně neumožňuje přímé odkazy na bity. `vector<bool>`používá jenom jeden bit na element, který lze odkazovat pomocí této třídy proxy serveru. Simulace odkazu však není kompletní, protože určitá přiřazení nejsou platná. Například protože adresu `vector<bool>::reference` objekt nelze vytvářet, následující kód, který používá [vektoru\<bool >:: operátor &#91; &#93;](http://msdn.microsoft.com/Library/97738633-690d-4069-b2d9-8c54104fbfdd) není správný:  
  
```cpp  
vector<bool> vb;  
// ...  
bool* pb = &vb[1]; // conversion error - do not use  
bool& refb = vb[1];   // conversion error - do not use  
```  
  
### <a name="member-functions"></a>Členské funkce  
  
|||  
|-|-|  
|[Překlopit](../standard-library/vector-bool-reference-flip.md)|Přemění logickou hodnotu prvku vektoru.|  
|[operátor bool](../standard-library/vector-bool-reference-operator-bool.md)|Poskytuje implicitní převod z `vector<bool>::reference` k `bool`.|  
|[operátor =](../standard-library/vector-bool-reference-operator-assign.md)|Přiřadí k bitu logickou hodnotu nebo hodnotu obsaženou referenčním prvkem.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví**: \<vektoru >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<vektor >](../standard-library/vector.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)

