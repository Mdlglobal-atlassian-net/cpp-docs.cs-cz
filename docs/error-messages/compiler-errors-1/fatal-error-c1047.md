---
title: "Závažná chyba C1047 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ddc117d1e83c635bfbc644606c6c8c6032ff4f8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fatal-error-c1047"></a>Závažná chyba C1047
Vytvoření objektu nebo knihovna souboru 'file' s kompilátoru starší než jiné objekty; opětovné sestavení staré objekty a knihovny  
  
 C1047 dojde, pokud objekt soubory nebo knihovny vytvořené s **/ltgc** jsou spojeny dohromady, ale kde vytvořené tyto soubory objektů nebo knihovny s různými verzemi sady nástrojů Visual C++.  
  
 To může nastat, když začít používat nové verze kompilátoru ale udělat čistou opětovné sestavení existující objekt soubory nebo knihovny.  
  
 Chcete-li vyřešit C1047, znovu vytvořit všechny soubory objektů nebo knihovny.