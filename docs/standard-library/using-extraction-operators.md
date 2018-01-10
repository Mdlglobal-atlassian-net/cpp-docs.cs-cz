---
title: "Používání operátorů extrakce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13019040c2deed5c9dd3549d7ab6207553a52bb8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-extraction-operators"></a>Používání operátorů extrakce
Operátor extrakce (`>>`), který je naprogramovaných pro všechny standardní datové typy C++, je nejjednodušší způsob, jak získat bajtů z objektu vstupního datového proudu.  
  
 Formátovaný text vstupní extraction – operátory závisí na mezera příchozí data hodnot. Toto je nepohodlná, když pole obsahuje více slova nebo když čísla oddělte čárkami. V takovém případě jeden alternativou je pomocí funkce neformátovaný vstupní člen [istream::getline](../standard-library/basic-istream-class.md#getline) číst blok textu s bílými oblasti zahrnuty, pak analyzovat blok s speciální funkce. Další možností je odvozena třídu vstupního datového proudu s členské funkce, jako `GetNextToken`, které můžete volat IStream on Request členy k extrahování a formátování dat znak.  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

