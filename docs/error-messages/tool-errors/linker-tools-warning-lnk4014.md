---
title: "Upozornění linkerů Lnk4014 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4014
dev_langs:
- C++
helpviewer_keywords:
- LNK4014
ms.assetid: 394903e9-3ded-4ea4-b7c0-a3535d4b4da4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8e0e0e87fb9c8e6006c62e07b7bb9b6435a22dd3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4014"></a>Upozornění linkerů LNK4014
Nelze najít objekt člen "objectname"  
  
 Nelze najít LIB `objectname` v knihovně.  
  
 **/Odebrat** a **/EXTRACT** možnosti vyžadují úplný název objektu člen, který má být odstraněn, nebo zkopíruje do souboru. Úplný název obsahuje cestu k souboru původní objekt. Pokud chcete zobrazit úplné názvy objektů člen v knihovně, použijte nástroje DUMPBIN [/ARCHIVEMEMBERS](../../build/reference/archivemembers.md) nebo LIB [/LIST](../../build/reference/managing-a-library.md).