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
ms.openlocfilehash: 4994b018cfbe8395f453cd5964f1d1733f3117e3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="27-data-environment"></a>2.7 Datové prostředí
Tato část představuje direktivu a několik klauzule řízení prostředí dat během provádění paralelní oblastech, následujícím způsobem:  
  
-   A **threadprivate** – direktiva (najdete v následující části) zajišťuje nastavit rozsah souboru, obor názvů nebo statický rozsah bloku proměnné místní na vlákno.  
  
-   Věty, které může být určen na direktivy k řízení sdílení atributy proměnných po dobu trvání konstrukce paralelní nebo sdílení práce jsou popsané v [části 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stránce 25.