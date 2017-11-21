---
title: 2.7.2.3 lastprivate | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 77f6a5c9-704f-4a88-8476-29db852ed800
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d4b6c904766699c2cccdd129f32461a5d612113d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="2723-lastprivate"></a>2.7.2.3 lastprivate
`lastprivate` Klauzule poskytuje větší funkce poskytované službou `private` klauzule. Syntaxe `lastprivate` klauzule vypadá takto:  
  
```  
lastprivate(variable-list)  
```  
  
 Proměnné zadané v *seznamu proměnné* mít `private` sémantiku klauzule. Když `lastprivate` klauzule se zobrazí na direktiva, která identifikuje konstrukce sdílení práce, hodnota jednotlivých `lastprivate` proměnné z postupně poslední iteraci smyčky přidružené nebo lexikálně poslední direktivu oddílu, je přiřazena k původní objekt proměnné. Proměnné, které nejsou přiřazenou hodnotu podle poslední iterace **pro** nebo **paralelní pro**, nebo lexikálně poslední část **části** nebo  **Parallel sections –** – direktiva, po konstruktu mít hodnoty neurčitou. Nepřiřazené podobjektů po konstruktu mít i hodnotu neurčitou.  
  
 Omezení, které mají `lastprivate` klauzule jsou následující:  
  
-   Všechna omezení pro `private` použít.  
  
-   Proměnná s typu třídy, který je zadaný jako `lastprivate` musí mít operátor přiřazení přístupný, jednoznačným kopírování.  
  
-   Proměnné, která jsou soukromá v rámci paralelní oblasti nebo která se zobrazují `reduction` klauzuli **paralelní** – direktiva nelze zadat v `lastprivate` klauzule ve sdílení práce direktiva, která se sváže s paralelní konstrukce.