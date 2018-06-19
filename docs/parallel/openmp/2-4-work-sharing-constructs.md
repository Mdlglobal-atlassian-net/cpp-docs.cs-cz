---
title: 2.4 konstrukce pro sdílení práce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689633"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukce pro sdílení práce
Sdílení práce konstrukt distribuuje provádění přidružený příkaz mezi členy seskupení, které ho. Direktivy sdílení práce není spusťte nové vláken a na položku pro sdílení práce konstrukt není žádné předpokládané bariéry.  
  
 Vytvoří pořadí sdílení práce a **bariéry** direktivy došlo musí být stejné pro každé vlákno v týmu.  
  
 OpenMP definuje následující konstrukce pro sdílení práce a tyto možnosti jsou popsány v následujících částech:  
  
-   **pro** – direktiva  
  
-   **části** – direktiva  
  
-   **jeden** – direktiva