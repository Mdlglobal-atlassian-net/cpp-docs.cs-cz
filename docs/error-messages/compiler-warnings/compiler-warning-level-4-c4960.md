---
title: "Kompilátoru (úroveň 4) upozornění C4960 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4960
dev_langs: C++
helpviewer_keywords: C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 160ae5a50d55ab0ebc89335aa3951aa781175feb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4960"></a>C4960 kompilátoru upozornění (úroveň 4)
'function' je příliš dlouhý pro být vytvořený profil  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil modul vstupní s funkcí větší než 65 535 pokyny. Velké funkce není k dispozici pro optimalizace na základě profilu.  
  
 Chcete-li vyřešit toto upozornění, zmenšete velikost funkce.