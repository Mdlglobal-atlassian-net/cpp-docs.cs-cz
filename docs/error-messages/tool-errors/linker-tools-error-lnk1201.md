---
title: "Chyba linkerů Lnk1201 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1201
dev_langs: C++
helpviewer_keywords: LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 344f56eb3097bad447d9a0b12a0c5aac6f68b119
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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