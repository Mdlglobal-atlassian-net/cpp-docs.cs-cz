---
title: "2.7 datové prostředí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e018a2c1b20bef640852ced913dc90266e733c06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="27-data-environment"></a>2.7 Datové prostředí
Tato část představuje direktivu a několik klauzule řízení prostředí dat během provádění paralelní oblastech, následujícím způsobem:  
  
-   A **threadprivate** – direktiva (najdete v následující části) zajišťuje nastavit rozsah souboru, obor názvů nebo statický rozsah bloku proměnné místní na vlákno.  
  
-   Věty, které může být určen na direktivy k řízení sdílení atributy proměnných po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsané v [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.