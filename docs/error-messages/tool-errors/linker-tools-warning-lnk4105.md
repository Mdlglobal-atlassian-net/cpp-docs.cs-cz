---
title: "Upozornění linkerů Lnk4105 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4105
dev_langs: C++
helpviewer_keywords: LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d64ff3756f709820c7e25b2986b8529a364139e2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4105"></a>Upozornění linkerů LNK4105
žádný argument zadaný s možnost "možnost"; ignoruje možnost  
  
 Toto upozornění se zobrazí pouze když [/Libpath](../../build/reference/libpath-additional-libpath.md) je možnost nastavena. Je-li zadán žádný adresář pomocí této možnosti linkeru ignoruje možnost a vygeneruje tuto zprávu upozornění.  
  
 Pokud není nutné přepsat existující nastavení prostředí knihovny, odeberte možnost/Libpath z příkazového řádku linkeru. Pokud chcete použít alternativní vyhledávání cestu pro knihovny, zadejte alternativní cestu, následující možnosti/Libpath.  
  
## <a name="example"></a>Příklad  
  
```  
link /libpath:c:\filepath\lib bar.obj  
```  
  
 by přímé linkeru pro vyhledání potřebných knihoven v `c:\filepath\lib` před vyhledáváním v výchozí umístění.