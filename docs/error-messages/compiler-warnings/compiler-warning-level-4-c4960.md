---
title: Kompilátoru (úroveň 4) upozornění C4960 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4960
dev_langs:
- C++
helpviewer_keywords:
- C4960
ms.assetid: 3b4ed286-9e8d-46f1-af0c-00ba669693a9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1281bc86ad363c02df5c39ed41f616a6fff1a9b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294424"
---
# <a name="compiler-warning-level-4-c4960"></a>C4960 kompilátoru upozornění (úroveň 4)
'function' je příliš dlouhý pro být vytvořený profil  
  
 Při použití [/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md), kompilátor zjistil modul vstupní s funkcí větší než 65 535 pokyny. Velké funkce není k dispozici pro optimalizace na základě profilu.  
  
 Chcete-li vyřešit toto upozornění, zmenšete velikost funkce.