---
title: "Kompilátoru (úroveň 4) upozornění C4960 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63849c73ffb96038058582b6cdc2519620290ccd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4960"></a>C4960 kompilátoru upozornění (úroveň 4)
'function' je příliš dlouhý pro být vytvořený profil  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil modul vstupní s funkcí větší než 65 535 pokyny. Velké funkce není k dispozici pro optimalizace na základě profilu.  
  
 Chcete-li vyřešit toto upozornění, zmenšete velikost funkce.