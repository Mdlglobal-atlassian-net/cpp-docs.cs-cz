---
title: "identity – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: utility/std::identity
dev_langs: C++
helpviewer_keywords:
- identity class
- identity structure
ms.assetid: 990756fd-7969-4b39-ad7e-0878e8dac8fd
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c9166383cbe79835cc3790826fc2e617eca22484
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="identity-structure"></a>identity – struktura
Struktura, která poskytuje definice typu jako parametr šablony.  
  
## <a name="syntax"></a>Syntaxe  
```  
struct identity {
   typedef Type type;
   Type operator()(const Type& left) const;
   };  
```  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`left`|Hodnota k identifikaci.|  
  
## <a name="remarks"></a>Poznámky  
 Třída obsahuje definici veřejné typu `type`, což je stejný jako parametr šablony typu. Se používá ve spojení s funkce šablony [dál](../standard-library/utility-functions.md#forward) zajistit, že parametr funkce není požadovaný typ.  
  
 K zajištění kompatibility se starším kódu, třída také definuje funkci identity `operator()` která její argument vrací `left`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<nástroj >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [\<nástroj >](../standard-library/utility.md)



