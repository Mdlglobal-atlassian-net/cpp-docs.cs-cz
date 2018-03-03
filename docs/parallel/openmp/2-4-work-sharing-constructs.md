---
title: "2.4 konstrukce pro sdílení práce | Microsoft Docs"
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
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 476e4e23b22527accaa095d80b827c95aed58c15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukce pro sdílení práce
Sdílení práce konstrukt distribuuje provádění přidružený příkaz mezi členy seskupení, které ho. Direktivy sdílení práce není spusťte nové vláken a na položku pro sdílení práce konstrukt není žádné předpokládané bariéry.  
  
 Vytvoří pořadí sdílení práce a **bariéry** direktivy došlo musí být stejné pro každé vlákno v týmu.  
  
 OpenMP definuje následující konstrukce pro sdílení práce a tyto možnosti jsou popsány v následujících částech:  
  
-   **pro** – direktiva  
  
-   **části** – direktiva  
  
-   **jeden** – direktiva