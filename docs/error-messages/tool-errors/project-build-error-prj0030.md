---
title: "Chyba sestavení projektu PRJ0030 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6fe537dd8e6705fd5e30929a2480eb1d9ef9119
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030
Makro rozšíření došlo k chybě. Vyhodnoťte rekurze překročena 32 úrovně pro $(makro).  
  
 Tato chyba je způsobená rekurze v makrech. Například pokud nastavíte **zprostředkující Directory** vlastnost (najdete v části [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md)) pro $(IntDir), bude mít rekurze.  
  
 Pokud chcete tuto chybu vyřešit, nejsou definovány vlastnosti z hlediska makra, které se používají k definování nebo makra.