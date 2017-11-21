---
title: "-Zc: trigraphs (náhrada trigraph) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /Zc
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- /Zc compiler options (C++)
- Conformance compiler options
- Zc compiler options (C++)
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 56068f6cb630ac12b9c8417940411616cec65c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="zctrigraphs-trigraphs-substitution"></a>/Zc:trigraphs (Náhrada trigraph)
Když **/Zc: trigraphs** není zadaný, kompilátor nahradí znak posloupnost trigraph pomocí odpovídající interpunkční znaménko. Chcete-li vypnout trigraph nahrazení, zadejte **/Zc:trigraphs-**. Ve výchozím nastavení **/Zc: trigraphs** je vypnutý.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Zc:trigraphs[-]  
```  
  
## <a name="remarks"></a>Poznámky  
 Trigraph se skládá ze dvou po sobě jdoucích otazníky ("??") následuje jedinečný třetí znak. Například kompilátor nahradí "?? = "trigraph pomocí znaku '#'. Použití trigraphs ve zdrojových souborech C, které používají znaková sada, která neobsahuje vhodné grafické reprezentace pro některé znaky interpunkce.  
  
 Seznam trigraph C/C++ a příklad, který ukazuje způsob použití trigraph najdete v tématu [trigraph](../../c-language/trigraphs.md).  
  
## <a name="see-also"></a>Viz také  
 [/Zc (shoda)](../../build/reference/zc-conformance.md)   
 [Trigraph](../../c-language/trigraphs.md)