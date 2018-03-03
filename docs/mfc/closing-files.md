---
title: "Zavírání souborů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27b1c59c952b022c7382db7d6b2dcb660cca2e9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="closing-files"></a>Zavírání souborů
Obvyklým v vstupně-výstupních operací, po dokončení se souboru, je třeba nejprve zavřít jeho.  
  
#### <a name="to-close-a-file"></a>Zavřete soubor  
  
1.  Použití **Zavřít** – členská funkce. Tato funkce zavře soubor systém souborů a v případě potřeby vyprázdní vyrovnávací paměti.  
  
 Pokud jste přidělili [cfile –](../mfc/reference/cfile-class.md) objekt rámec (jak je ukázáno v [otevírání souborů](../mfc/opening-files.md)), bude objektu automaticky zavřít a pak zničený, když probíhá mimo rozsah. Všimněte si, že odstranění `CFile` objekt neodstraní fyzického souboru v systému souborů.  
  
## <a name="see-also"></a>Viz také  
 [Soubory](../mfc/files-in-mfc.md)

