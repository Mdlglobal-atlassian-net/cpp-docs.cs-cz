---
title: "Upozornění linkerů Lnk4204 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4204
dev_langs: C++
helpviewer_keywords: LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f9b2d9611192fe4afe01d178ac3af5fcc8ccc42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4204"></a>Upozornění linkerů LNK4204
'název souboru' chybí ladicí informace pro odkazování na modulu; propojování objektů, jako kdyby žádné informace o ladění  
  
 Na soubor .pdb má chybný podpis. Linkeru bude odkaz objektu bez informace o ladění. Možná budete chtít znovu zkompiluje soubor objekt pomocí [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) možnost.  
  
 LNK4204 může dojít, pokud některé objekty v knihovně odkazovat na soubor, který již existuje. To se může stát při opětovném sestavování řešení, například; soubor objektu může být odstraněn a není znovu sestavit z důvodu chyby kompilace. V takovém případě buď kompilovat s **/Z7**, nebo **/Fd**, chcete-li aktualizovat objekty, které se odkazují do jednoho souboru na knihovny (které není výchozí název souboru PDB).  Další informace najdete v tématu [/Fd (název souboru databáze programu)](../../build/reference/fd-program-database-file-name.md).  Ujistěte se, že PDB uloží s knihovnou pokaždé, když jsou aktualizovány v systému správy zdrojů.