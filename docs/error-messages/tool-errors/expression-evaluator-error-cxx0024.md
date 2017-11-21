---
title: "CXX0024 Chyba vyhodnocování výrazu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0024
dev_langs: C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 386e04d8aa1655896b77f8492d7929778edd6109
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>Chyba při vyhodnocování výrazu CXX0024
operace musí l-value  
  
 Výraz, který nelze vyhodnotit na hodnotu l byl zadán pro operaci, která vyžaduje l hodnota.  
  
 L – hodnota (nazývané, protože se zobrazí na levé straně příkazu přiřazení) je výraz, který odkazuje na umístění paměti.  
  
 Například `buffer[count]` je platný l hodnota, protože odkazuje na konkrétní paměti umístění. Logické porovnání `zed != 0` není platná hodnota l, protože se vyhodnotí na hodnotu TRUE nebo FALSE, ne na adresu paměti.  
  
 Tato chyba je stejný jako CAN0024.