---
title: "Chyba linkerů Lnk1140 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1140
dev_langs: C++
helpviewer_keywords: LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f19c69fad3ac9cc25863bfe8cd4de8100dbf372e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140
příliš mnoho modulů pro databázi programu; odkaz s/pdb: žádné  
  
 Projekt obsahuje více než 4096 moduly.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Znovu připojit pomocí [/pdb: žádný](../../build/reference/pdb-use-program-database.md).  
  
2.  Některé moduly kompilovat bez ladění informace.  
  
3.  Snižte počet modulů.