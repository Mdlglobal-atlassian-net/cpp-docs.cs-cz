---
title: "2.7.2.4 sdílené | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c9c5d653-58fc-4620-ab0a-443ac4f8ba2e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4320a3df64d8056cf1c8657acc78281f56cd1c85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="2724-shared"></a>2.7.2.4 shared
Tuto klauzuli sdílí proměnné, které se zobrazují v *seznamu proměnné* mezi všechna vlákna v týmu. Všechna vlákna v rámci týmu přístup k oblasti úložiště pro **sdílené** proměnné.  
  
 Syntaxe **sdílené** klauzule vypadá takto:  
  
```  
shared(variable-list)  
```