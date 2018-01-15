---
title: "money_base – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: xlocmon/std::money_base
dev_langs: C++
helpviewer_keywords: money_base class
ms.assetid: 1a303c15-9272-4f26-ae16-dcf43a0fd38a
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9b3243807c407fa4deeb30b8f35aa6f7acb13707
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="moneybase-class"></a>money_base – třída
Třída popisuje výčet a strukturou společné pro všechny specializací třídy šablony [moneypunct](../standard-library/moneypunct-class.md).  
  
## <a name="syntax"></a>Syntaxe  
```    
struct pattern
{
   char field[_PATTERN_FIELD_SIZE];
};  
```  
## <a name="remarks"></a>Poznámky  
 Výčet **část** popisuje možné hodnoty v elementech pole pole ve struktuře vzoru. Hodnoty **část** jsou:  
  
- **žádný** odpovídat počtu nula či více mezery nebo nic vygenerování.  
  
- **přihlašovací** odpovídat nebo vygenerování znaménkem kladné a záporné.  
  
- **místo** odpovídat počtu nula či více mezery nebo vygenerování mezerou.  
  
- **symbol** odpovídat nebo vygenerování symbolu měny.  
  
- **Hodnota** odpovídat nebo vygenerování peněžní hodnota.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<národní prostředí >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



