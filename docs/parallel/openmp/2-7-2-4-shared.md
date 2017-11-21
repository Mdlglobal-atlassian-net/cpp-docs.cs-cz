---
title: "2.7.2.4 sdílené | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 974f534003455ccd750ddc1b7c1f3c28b220f1b4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="2724-shared"></a>2.7.2.4 shared
Tuto klauzuli sdílí proměnné, které se zobrazují v *seznamu proměnné* mezi všechna vlákna v týmu. Všechna vlákna v rámci týmu přístup k oblasti úložiště pro **sdílené** proměnné.  
  
 Syntaxe **sdílené** klauzule vypadá takto:  
  
```  
shared(variable-list)  
```