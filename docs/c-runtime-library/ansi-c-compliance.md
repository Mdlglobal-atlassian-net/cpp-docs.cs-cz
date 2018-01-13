---
title: "Kompatibilita se specifikací ANSI C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Ansi
dev_langs: C++
helpviewer_keywords:
- underscores, leading
- compatibility [C++], ANSI C
- compliance with ANSI C
- conventions [C++], Microsoft extensions
- underscores
- naming conventions [C++], Microsoft library
- ANSI [C++], C standard
- Microsoft extensions naming conventions
ms.assetid: 6be271bf-eecf-491a-a928-0ee2dd60e3b9
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f9c8831ef19e14d5d65ae39abde9af8ed669bb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ansi-c-compliance"></a>Kompatibilita se specifikací ANSI C
Zásady vytváření názvů pro všechny identifikátory specifické pro společnost Microsoft v běhu systému (například funkce, makra, konstanty, proměnné a definic typů) je kompatibilní se specifikací ANSI. V této dokumentaci je žádné běhové funkce, který dodržuje standardy ANSI/ISO C poznamenat, že je ANSI kompatibilní. Aplikace standardu ANSI měli používat jenom tyto funkce kompatibilní ANSI.  
  
 Názvy funkce specifické pro společnost Microsoft a globální proměnné začít s jedním podtržítkem. Názvy těchto lze přepsat pouze místně v rámci oboru vašeho kódu. Například když zahrnete Microsoft běhu hlavičkových souborů, můžete stále místně přepsat funkce specifické pro společnost Microsoft s názvem `_open` deklarováním místní proměnné se stejným názvem. Tento název pro globální funkce nebo – globální proměnná však nelze použít.  
  
 Názvy makra specifické pro společnost Microsoft a manifestu konstanty začít dvě podtržítka nebo s jedním úvodní podtržítkem bezprostředně následované velké písmeno. Rozsah tyto identifikátory je absolutní. Například nemůžete použít identifikátor specifické pro společnost Microsoft **_UPPER** z tohoto důvodu.  
  
## <a name="see-also"></a>Viz také  
 [Kompatibilita](../c-runtime-library/compatibility.md)