---
title: "Neúplné typy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- void keyword [C], incomplete
- types [C], incomplete
- incomplete types
- unions, incomplete
- arrays [C], incomplete types
- void keyword [C]
- structures, incomplete
ms.assetid: 01bc0cf6-9fa7-458c-9371-ecbe54ea6aee
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2dd7ab170717cb0e20d71ad4e62e2cbc03483fbf
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="incomplete-types"></a>Neúplné typy
Nekompletní typ je typ, který popisuje identifikátor, ale neobsahuje informace potřebné k určení jeho velikosti. „Nekompletní typ“ může být:  
  
-   Typ struktury, jejíž členy ještě nebyly určeny.  
  
-   Typ sjednocení, jehož členy ještě nebyly určeny.  
  
-   Typ pole, jehož rozměry ještě nebyly určeny.  
  
 Typ void je nekompletním typem, který nelze dokončit. Chcete-li dokončit nekompletní typ, zadejte chybějící informace. Následující příklad ukazuje, jak vytvořit a dokončit nekompletní typy.  
  
-   Chcete-li vytvořit nekompletní typ struktury, deklarujte typ struktury bez zadání jejích členů. V tomto příkladu ukazatel `ps` ukazuje na nekompletní typ struktury s názvem `student`.  
  
    ```  
    struct student *ps;  
    ```  
  
-   Chcete-li dokončit nekompletní typ struktury, deklarujte dále ve stejném oboru stejný typ struktury se zadanými členy, například  
  
    ```  
    struct student  
    {  
        int num;  
    }                   /* student structure now completed */  
    ```  
  
-   Chcete-li vytvořit nekompletní typ pole, deklarujte typ pole bez určení počtu opakování. Příklad:  
  
    ```  
    char a[];  /* a has incomplete type */  
    ```  
  
-   Chcete-li dokončit nekompletní typ pole, deklarujte stejný název dále ve stejném oboru se zadaným počtem opakování, například  
  
    ```  
    char a[25]; /* a now has complete type */  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Deklarace a typy](../c-language/declarations-and-types.md)