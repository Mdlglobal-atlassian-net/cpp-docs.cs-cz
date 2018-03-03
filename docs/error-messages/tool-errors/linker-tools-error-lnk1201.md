---
title: "Chyba linkerů Lnk1201 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 44e2ad811645889cd655bf297f6f8b9492574def
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1201"></a>Chyba linkerů LNK1201
Chyba při zápisu do databáze programu 'název souboru'; kontrolovat nedostatek místa na disku, neplatná cesta nebo nemáte dostatečná oprávnění  
  
 Odkaz nemůže zapisovat do databáze programu (PDB) pro výstupní soubor.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  Soubor je poškozený. Odstraňte soubor PDB a znovu připojit.  
  
2.  Není dostatek místa na disku pro zápis souboru.  
  
3.  Jednotka není k dispozici, pravděpodobně kvůli potížím se sítí.  
  
4.  Ladicí program je aktivní na aplikaci, kterou chcete propojit.  
  
5.  Nedostatek místa na haldy.  V tématu [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) Další informace.