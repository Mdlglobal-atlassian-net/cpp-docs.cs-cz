---
title: "Diagnostika vytištěná podle funkce assert | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 78b64200-520d-40da-9a61-71553f411d4f
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d6e5ea4e5f8bae3fda190ac7a7136035aea0c948
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="diagnostic-printed-by-the-assert-function"></a>Diagnostika vytištěná podle funkce assert
**ANSI 4.2** diagnostiky tištěné a chování při ukončení **assert** – funkce  
  
 **Assert** funkce vytiskne diagnostické zprávy a volání **abort** rutiny, pokud výraz hodnotu false (0). Diagnostická zpráva má tvar  
  
 **Kontrolní výraz systému se nezdařilo**: *výraz***, soubor** *filename***, řádku** *linenumber*  
  
 kde název souboru je název zdrojového souboru a číslo řádku je číslo řádku výrazu, který v tomto zdrojovém souboru selhal. V případě, že je výraz pravdivý (nenulový), nedojde k žádné akci.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)