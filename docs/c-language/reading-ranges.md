---
title: Čtení rozsahů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a8ebad4bfda77238ad8c861410e2af5453df73af
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383641"
---
# <a name="reading-ranges"></a>Čtení rozsahů
**ANSI 4.9.6.2** výklad znak pomlčka (-), který je ani první ani poslední znak v scanlist pro % [převod v `fscanf` – funkce  
  
 Následující řádek  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 přečte libovolný počet znaků v rozsahu A – Ž do řetězce do které `strptr` body.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)