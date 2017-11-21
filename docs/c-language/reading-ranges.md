---
title: "Čtení rozsahů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 96748c24fbf1e5adfebb72ba809533afeafebe38
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="reading-ranges"></a>Čtení rozsahů
**ANSI 4.9.6.2** výklad znak pomlčka (-), který je ani první ani poslední znak v scanlist pro % [převod v `fscanf` – funkce  
  
 Následující řádek  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 přečte libovolný počet znaků v rozsahu A – Ž do řetězce do které `strptr` body.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)