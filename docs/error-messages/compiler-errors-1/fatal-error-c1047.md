---
title: Závažná chyba C1047 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce88321173ee2c8cc286f18d8ab8f1bf5ec98e13
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1047"></a>Závažná chyba C1047
Vytvoření objektu nebo knihovna souboru 'file' s kompilátoru starší než jiné objekty; opětovné sestavení staré objekty a knihovny  
  
 C1047 dojde, pokud objekt soubory nebo knihovny vytvořené s **/ltgc** jsou spojeny dohromady, ale kde vytvořené tyto soubory objektů nebo knihovny s různými verzemi sady nástrojů Visual C++.  
  
 To může nastat, když začít používat nové verze kompilátoru ale udělat čistou opětovné sestavení existující objekt soubory nebo knihovny.  
  
 Chcete-li vyřešit C1047, znovu vytvořit všechny soubory objektů nebo knihovny.