---
title: Chyba linkerů Lnk1140 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1140
dev_langs:
- C++
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc0d59589a1882aca4ef2deb419e1e4f1081e52b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1140"></a>Chyba linkerů LNK1140
příliš mnoho modulů pro databázi programu; odkaz s/pdb: žádné  
  
 Projekt obsahuje více než 4096 moduly.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li odstranit pomocí následující možná řešení  
  
1.  Znovu připojit pomocí [/pdb: žádný](../../build/reference/pdb-use-program-database.md).  
  
2.  Některé moduly kompilovat bez ladění informace.  
  
3.  Snižte počet modulů.