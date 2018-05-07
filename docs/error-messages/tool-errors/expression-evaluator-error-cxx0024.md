---
title: CXX0024 Chyba vyhodnocování výrazu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 50a07297ddabf269b003a1f14d967d1187fea96d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0024"></a>Chyba při vyhodnocování výrazu CXX0024
operace musí l-value  
  
 Výraz, který nelze vyhodnotit na hodnotu l byl zadán pro operaci, která vyžaduje l hodnota.  
  
 L – hodnota (nazývané, protože se zobrazí na levé straně příkazu přiřazení) je výraz, který odkazuje na umístění paměti.  
  
 Například `buffer[count]` je platný l hodnota, protože odkazuje na konkrétní paměti umístění. Logické porovnání `zed != 0` není platná hodnota l, protože se vyhodnotí na hodnotu TRUE nebo FALSE, ne na adresu paměti.  
  
 Tato chyba je stejný jako CAN0024.