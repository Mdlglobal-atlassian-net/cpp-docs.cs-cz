---
title: Upozornění linkerů Lnk4105 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4105
dev_langs:
- C++
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ffdd8953e08f38d36bdfc2e68ad6cb8e06fb85b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33304411"
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