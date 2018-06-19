---
title: Chyba linkerů Lnk1312 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1312
dev_langs:
- C++
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 748276ed8fa459c41174f23d32bcef127cbdd510
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33300443"
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