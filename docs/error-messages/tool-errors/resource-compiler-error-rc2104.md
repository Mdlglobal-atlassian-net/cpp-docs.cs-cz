---
title: Chyba kompilátoru prostředků RC2104 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC2104
dev_langs:
- C++
helpviewer_keywords:
- RC2104
ms.assetid: 792a3bd8-cb4c-4817-b288-4ce37082b582
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 28beaad95cc33d8b014b22035f9ed641f1b6ab6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-error-rc2104"></a>Chyba kompilátoru prostředků RC2104
Nedefinovaný název – klíčové slovo nebo klíč: klíč  
  
 Zadané klíčové slovo nebo název klíče není definován.  
  
 Tato chyba je často způsobené překlepem v definici prostředků nebo v souboru zahrnuté záhlaví. Můžete se také jednat chybí záhlaví souboru.  
  
 Chcete-li vyřešit problém, vyhledejte soubor hlaviček, který by měl obsahovat definované – klíčové slovo nebo název klíče a ověřte, že je součástí souboru prostředků a že – klíčové slovo nebo klíč název je napsán správně. Pokud váš projekt byl vytvořen s předkompilovaných hlaviček a následně odebrat, ujistěte se, že se soubor prostředků stále zahrnuje všechny požadované hlavičky.  
  
 Ověření definovaná klíčová slova a názvy klíčů v souboru prostředků v sadě Visual Studio, otevřete **zobrazení prostředků** okno – na řádku nabídek zvolte **zobrazení**, **zobrazení prostředků**– a potom otevřete místní nabídku pro soubor .rc a zvolte **symboly prostředků** zobrazíte seznam definovaných symbolů. Pokud chcete upravit zahrnuté hlavičky, otevřete místní nabídku pro soubor .rc a zvolte **prostředek zahrnuje**.  
  
 Pokud narazíte na tuto zprávu:  
  
```  
undefined keyword or key name: MFT_STRING   
```  
  
 Otevřete \MCL\MFC\Include\AfxRes.h a přidejte tuto include – direktiva:  
  
```  
#include <winresrc.h>  
```