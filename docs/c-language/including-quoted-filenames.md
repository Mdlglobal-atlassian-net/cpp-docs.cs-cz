---
title: "Včetně názvů souboru v uvozovkách | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 789a047e-ea38-4c99-b71d-a2ad9c81daee
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 75b9e308fec394825b3113a716ead2c93e9bb290
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="including-quoted-filenames"></a>Zahrnutí názvů souboru v uvozovkách
**ANSI 3.8.2** podporu uvozovkách názvy pro includable zdrojové soubory  
  
 Pokud zadáte jednoznačnou kompletní specifikaci cesty k souboru zahrnutí mezi dvě sady dvojitých uvozovek (" "), preprocesor prohledá pouze specifikaci cesty a ignoruje standardní adresáře.  
  
 Pro zadané jako soubory zahrnout [#include](../preprocessor/hash-include-directive-c-cpp.md) "cesta specifikace", adresář hledání začíná adresáře nadřazeném souboru a potom pokračuje prostřednictvím adresáře všechny soubory nadřazený. Hledání tedy začíná relativně vzhledem k adresáři obsahujícímu zdrojový soubor, který se právě zpracovává. Pokud není dostupný žádný nadřazený soubor a soubor nebyl nalezen, vyhledávání bude pokračovat, jako kdyby měla název souboru uzavřené v lomených závorkách.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy předběžného zpracování](../c-language/preprocessing-directives.md)