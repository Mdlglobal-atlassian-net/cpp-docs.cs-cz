---
title: Závažná chyba C1067 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ac7084e92f7f2ed496a4c1572e94a4fa46862f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1067"></a>Závažná chyba C1067
omezení kompilátoru: byl překročen limit 64 kB na velikost, typ záznamu  
  
 Tato chyba mohla nastat, pokud symbol má upravený název překročení 247 znaků.  Pokud chcete vyřešit, zkraťte název symbolu.  
  
 Pokud kompilátor vygeneruje informace o ladění, vysílá záznamů typu k definování typů došlo ve zdrojovém kódu.  Například záznamů typu zahrnují jednoduché struktury a seznamy argumentů funkcí.  Některé z těchto typů záznamů může být velký seznamy.  
  
 Je omezena na 64 kB na velikost libovolného typu záznamu.  Pokud dojde k překročení tohoto limitu 64 tisíc této chybě dojde.  
  
 C1067 může také nastat, pokud existuje mnoho symbolů s dlouhé názvy nebo pokud třída, struktura nebo union má příliš mnoho členů.