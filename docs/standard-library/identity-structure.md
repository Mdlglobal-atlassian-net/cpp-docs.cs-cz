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
ms.openlocfilehash: 280ce6a24e1de9d0e7206e7f9e5b0d896d8c6787
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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



