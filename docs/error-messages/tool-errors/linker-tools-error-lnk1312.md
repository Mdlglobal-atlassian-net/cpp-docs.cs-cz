---
title: "Chyba linkerů Lnk1312 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1312
dev_langs: C++
helpviewer_keywords: LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0fc7bf47ff05f817b36ff9ff641fe7823aa38d9a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1312"></a>Chyba linkerů LNK1312
Neplatný nebo poškozený soubor: nelze importovat sestavení  
  
 Při vytváření sestavení, soubor než modulu nebo sestavení zkompilovaného s **/CLR** byl předán **/ASSEMBLYMODULE** – možnost linkeru.  Pokud předány soubor objektu k **/ASSEMBLYMODULE**, stačí předat objekt přímo na linkeru, místo do **/ASSEMBLYMODULE**.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří souboru .obj.  
  
```  
// LNK1312.cpp  
// compile with: /clr /LD  
public ref class A {  
public:  
   int i;  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje LNK1312.  
  
```  
// LNK1312_b.cpp  
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj  
// LNK1312 error expected  
public ref class M {};  
```