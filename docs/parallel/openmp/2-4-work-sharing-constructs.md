---
title: "2.4 konstrukce pro sdílení práce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5353bc51f6a701201520f700057ef76ce7778191
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukce pro sdílení práce
Sdílení práce konstrukt distribuuje provádění přidružený příkaz mezi členy seskupení, které ho. Direktivy sdílení práce není spusťte nové vláken a na položku pro sdílení práce konstrukt není žádné předpokládané bariéry.  
  
 Vytvoří pořadí sdílení práce a **bariéry** direktivy došlo musí být stejné pro každé vlákno v týmu.  
  
 OpenMP definuje následující konstrukce pro sdílení práce a tyto možnosti jsou popsány v následujících částech:  
  
-   **pro** – direktiva  
  
-   **části** – direktiva  
  
-   **jeden** – direktiva