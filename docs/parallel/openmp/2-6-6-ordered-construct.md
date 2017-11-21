---
title: "2.6.6 ordered – konstrukce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 690db7cbc03e9aa9a3b4780dd2b115812c31f984
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="266-ordered-construct"></a>2.6.6 ordered – konstrukce
Následující strukturovaných bloku **seřazené** – direktiva se spouštějí v tom pořadí, ve kterém by byl proveden opakování ve smyčce sekvenční. Syntaxe **seřazené** – Direktiva vypadá takto:  
  
```  
#pragma omp ordered new-linestructured-block  
```  
  
 **Seřazené** – direktiva musí být v dynamické rozsah **pro** nebo **paralelní pro** vytvořit. **Pro** nebo **paralelní pro** direktivy, ke kterému **seřazené** konstrukce vazby musí mít **seřazené** klauzule zadat, jak je popsáno v [Části 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) na stránce 11. Za běhu **pro** nebo **paralelní pro** vytvořit s **seřazené** klauzuli **seřazené** výhradně v provedení konstrukce pořadí, ve kterém by být prováděna v sekvenčních provádění smyčky.  
  
 Omezení **seřazené** – direktiva jsou následující:  
  
-   Iterace smyčky pomocí **pro** konstrukce nesmí více než jednou spusťte seřazené směrnice a nesmí provést, více než jeden **seřazené** – direktiva.