---
title: Upozornění linkerů Lnk4221 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4221
dev_langs:
- C++
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8906c4308b8586d5b1312739921f58063e820deb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4221"></a>Upozornění linkerů LNK4221
Tento soubor objektu nedefinuje dříve definován veřejné symboly, proto ji nebude možné použít všechny operace odkazu, který využívá tuto knihovnu  
  
 Vezměte v úvahu následující fragmenty kódu dva.  
  
```  
// a.cpp  
#include <atlbase.h>  
```  
  
```  
// b.cpp  
#include <atlbase.h>  
int function()  
{  
   return 0;  
}  
  
```  
  
 Pro zkompilování soubory a vytvořte dva soubory objektu, spusťte **cl /c a.cpp b.cpp** na příkazovém řádku. Pokud jste soubory objektů spuštěním **propojit/lib /out:test.lib a.obj b.obj**, zobrazí se upozornění LNK4221. Pokud jste objekty spuštěním **propojit/lib /out:test.lib b.obj a.obj**, nebudete dostávat upozornění.  
  
 Druhý scénář se objeví žádné upozornění, protože linkeru funguje způsobem last-in ven (LIFO). V prvního scénáře b.obj se zpracují dříve, než a.obj a a.obj nemá žádné nové symboly přidat. Podle instruující linkeru nejprve zpracovat a.obj, se můžete vyhnout upozornění.  
  
 Obvyklou příčinou této chyby je, pokud dva zdrojové soubory, zadejte možnost [/Yc (Vytvořit předkompilovaný hlavičkový soubor)](../../build/reference/yc-create-precompiled-header-file.md) se stejným názvem záhlaví soubor zadaný v **předkompilovaných hlaviček** pole. Obvyklou příčinou tohoto problému se zabývá stdafx.h od ve výchozím nastavení, stdafx.cpp zahrnuje stdafx.h a nebudou přidány žádné nové symboly. Pokud jiný zdrojový soubor obsahuje stdafx.h s **/Yc** a zpracování souboru .obj související než stdafx.obj, linkeru vyvolá výjimku LNK4221.  
  
 Jedním ze způsobů, chcete-li vyřešit tento problém je Ujistěte se, že pro každý předkompilovaných hlaviček, je pouze jeden zdrojový soubor, který zahrnuje její **/Yc**. Všechny ostatní zdrojové soubory musíte použít předkompilovaných hlaviček. Další informace o tom, jak změnit toto nastavení najdete v tématu [/Yu (Použít předkompilovaný hlavičkový soubor)](../../build/reference/yu-use-precompiled-header-file.md).