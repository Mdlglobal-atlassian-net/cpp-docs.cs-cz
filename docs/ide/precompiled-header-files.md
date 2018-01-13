---
title: "Předkompilované soubory hlaviček | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdafx.h
dev_langs: C++
helpviewer_keywords:
- stdafx.h
- PCH files, file descriptions
- .pch files, file descriptions
- precompiled header files, file descriptions
- stdafx.cpp
ms.assetid: 8228d87a-5609-41f3-9697-b16094c000e5
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1208b000f57397764277cc0a43e223f7c781a06e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="precompiled-header-files"></a>Předkompilované soubory hlaviček
Tyto soubory se používají k vytvoření souboru předkompilovaných hlaviček *Projname*.pch a předkompilovaných typy souborů Stdafx.obj.  
  
 Tyto soubory jsou umístěny v *Projname* adresáře. V Průzkumníku řešení Stdafx.h nachází ve složce soubory hlaviček a Stdafx.cpp je umístěn ve složce zdrojové soubory.  
  
|Název souboru|Popis|  
|---------------|-----------------|  
|Stdafx.h|Vložené soubory pro standardní systému zahrnout soubory a pro konkrétní projekt zahrnout soubory, které se často používají, ale jsou zřídka změněny.<br /><br /> By nemělo definovat nebo nedefinované žádné _AFX_NO_XXX v stdafx.h; najdete v článku znalostní báze Knowledge Base "PRB: dojde k problémům při definování _AFX_NO_XXX". Články znalostní báze můžete vyhledat v MSDN nebo v [http:// support.microsoft.com/](http://%20support.microsoft.com/).|  
|Stdafx.cpp|Obsahuje direktivy preprocesoru `#include "stdafx.h"` a přidá zahrnout soubory pro předkompilované typy. Předkompilované soubory libovolného typu, včetně souborů hlavičky, umožňují rychlejší kompilaci omezením kompilace pouze na tyto soubory, které je vyžadují. Po prvním sestavení projektu, si všimnete sestavení mnohem rychlejší další z důvodu přítomnosti soubory předkompilovaných hlaviček.|  
  
## <a name="see-also"></a>Viz také  
 [Typy souborů vytvořených pro projekty Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Práce s vlastnostmi projektu](../ide/working-with-project-properties.md)