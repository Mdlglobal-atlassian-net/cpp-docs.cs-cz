---
title: Chyba sestavení projektu PRJ0030 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bf1c9137f8c4ed0d80955eef38b07ea86204a5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030
Makro rozšíření došlo k chybě. Vyhodnoťte rekurze překročena 32 úrovně pro $(makro).  
  
 Tato chyba je způsobená rekurze v makrech. Například pokud nastavíte **zprostředkující Directory** vlastnost (najdete v části [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md)) pro $(IntDir), bude mít rekurze.  
  
 Pokud chcete tuto chybu vyřešit, nejsou definovány vlastnosti z hlediska makra, které se používají k definování nebo makra.