---
title: "součást | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.component
- component_CPP
dev_langs: C++
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ba0c7211ad7d859dfaf44a9e7843fa6984ec167a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="component"></a>komponenta
Řídí shromažďování informací o procházení nebo závislostech ze zdrojových souborů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      #pragma component( browser, { on | off }[, references [, name ]] )  
#pragma component( minrebuild, on | off )  
#pragma component( mintypeinfo, on | off )  
```  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="browser"></a>Prohlížeč  
 Toto shromažďování lze zapnout nebo vypnout a lze určit konkrétní názvy, které mají být při shromažďování informací ignorovány.  
  
 Použití zapnutí nebo vypnutí řídí shromažďování informací procházení z direktivy pragma forward. Příklad:  
  
```  
#pragma component(browser, off)  
```  
  
 zastaví shromažďování informací o procházení kompilátorem.  
  
> [!NOTE]
>  Zapnout shromažďování informací o procházení s Tato direktiva pragma [informacemi o procházení musí být nejprve povoleno](../build/reference/building-browse-information-files-overview.md).  
  
 **Odkazy** možnost lze použít bez ohledu *název* argument. Pomocí **odkazy** bez *název* Zapne nebo vypne shromažďování odkazy (Další informace, procházet se mají shromažďovat, ale i nadále). Příklad:  
  
```  
#pragma component(browser, off, references)  
```  
  
 zastaví shromažďování informací o odkazech kompilátorem.  
  
 Pomocí **odkazy** s *název* a **vypnout** brání odkazy na *název* zobrazování v okně Procházet informace. Tuto syntaxi použijte, pokud chcete ignorovat názvy a typy, které vás nezajímají, a pokud chcete zmenšit velikost souborů s informacemi o procházení. Příklad:  
  
```  
#pragma component(browser, off, references, DWORD)  
```  
  
 ignoruje odkazy na **DWORD** od tohoto okamžiku. Chcete-li shromažďování odkazy na `DWORD` zpět na pomocí **na**:  
  
```  
#pragma component(browser, on, references, DWORD)  
```  
  
 Toto je jediný způsob, jak obnovit shromažďování odkazy na *název*; je potřeba explicitně zapnout žádné *název* , je vypnuto.  
  
 Preprocesor zabránit rozšíření *název* (jako je například rozšíření **NULL** k **0**), uvést v uvozovkách ho:  
  
```  
#pragma component(browser, off, references, "NULL")  
```  
  
## <a name="minimal-rebuild"></a>Minimální opětovné sestavení  
 Funkce minimálního opětovného sestavení jazyka Visual C++ vyžaduje, aby kompilátor vytvořil a uložil informace o závislostech tříd jazyka C++, což zabírá místo na disku. Chcete-li ušetřit místo na disku, můžete použít `#pragma component( minrebuild, off )` vždy, když nemusíte shromažďovat informace o závislostech, například v neměnné hlavičkových souborů. Vložit `#pragma component(minrebuild, on)` po neměnné třídy, chcete-li kolekce závislost zpět na.  
  
## <a name="reduce-type-information"></a>Omezení informací o typech  
 **Mintypeinfo** možnost snižuje ladicí informace pro oblast zadán. Objem těchto informací je značný a ovlivňuje soubory .pdb a .obj. V oblasti mintypeinfo nelze ladit třídy a struktury. Použití možnosti mintypeinfo může být užitečné, chcete-li zabránit následujícímu upozornění:  
  
```  
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information  
```  
  
 Další informace najdete v tématu [povolit minimální opětovné sestavení](../build/reference/gm-enable-minimal-rebuild.md) (nebo Gm) – možnost kompilátoru.  
  
## <a name="see-also"></a>Viz také  
 [Direktivy pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)