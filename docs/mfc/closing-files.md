---
title: Zavírání souborů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bd910ae4cb514cda07dd319f37a05a32712909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341023"
---
# <a name="closing-files"></a>Zavírání souborů
Obvyklým v vstupně-výstupních operací, po dokončení se souboru, je třeba nejprve zavřít jeho.  
  
#### <a name="to-close-a-file"></a>Zavřete soubor  
  
1.  Použití **Zavřít** – členská funkce. Tato funkce zavře soubor systém souborů a v případě potřeby vyprázdní vyrovnávací paměti.  
  
 Pokud jste přidělili [cfile –](../mfc/reference/cfile-class.md) objekt rámec (jak je ukázáno v [otevírání souborů](../mfc/opening-files.md)), bude objektu automaticky zavřít a pak zničený, když probíhá mimo rozsah. Všimněte si, že odstranění `CFile` objekt neodstraní fyzického souboru v systému souborů.  
  
## <a name="see-also"></a>Viz také  
 [Soubory](../mfc/files-in-mfc.md)

