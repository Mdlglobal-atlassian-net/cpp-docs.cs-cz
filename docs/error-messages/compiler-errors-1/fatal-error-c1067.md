---
title: "Závažná chyba C1067 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8889ccbfcac31917948da719444dab68a2d1b9c6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1067"></a>Závažná chyba C1067
omezení kompilátoru: byl překročen limit 64 kB na velikost, typ záznamu  
  
 Tato chyba mohla nastat, pokud symbol má upravený název překročení 247 znaků.  Pokud chcete vyřešit, zkraťte název symbolu.  
  
 Pokud kompilátor vygeneruje informace o ladění, vysílá záznamů typu k definování typů došlo ve zdrojovém kódu.  Například záznamů typu zahrnují jednoduché struktury a seznamy argumentů funkcí.  Některé z těchto typů záznamů může být velký seznamy.  
  
 Je omezena na 64 kB na velikost libovolného typu záznamu.  Pokud dojde k překročení tohoto limitu 64 tisíc této chybě dojde.  
  
 C1067 může také nastat, pokud existuje mnoho symbolů s dlouhé názvy nebo pokud třída, struktura nebo union má příliš mnoho členů.