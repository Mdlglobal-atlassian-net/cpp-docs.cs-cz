---
title: "Kompilátoru (úroveň 1) upozornění C4691 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4691
dev_langs:
- C++
helpviewer_keywords:
- C4691
ms.assetid: 722133d9-87f6-46c1-9e86-9825453d6999
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 17673ee3e65d2e0cd0d989c56759b62de38f5fdc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4691"></a>C4691 kompilátoru upozornění (úroveň 1)
'type': v neregistrované sestavení 'file' typem definovaným v aktuální jednotku překlad místo toho použít byl očekáván typ odkazuje  
  
 Metadata souboru, který obsahuje původní definici typu neodkazuje a kompilátor používá definici místního typu.  
  
 V případě, kde jsou znovu sestavit *soubor*, C4691 můžete ignorovat nebo vypnuté s – Direktiva pragma [upozornění](../../preprocessor/warning.md).  To znamená pokud soubor, který vytváříte je stejný jako souboru, kde se předpokládá, že kompilátor najít definici typu, můžete ignorovat C4691.  
  
 Ale neočekávanému chování může dojít, pokud kompilátor používá definici, který nepochází od stejného sestavení, který se odkazuje v metadatech; Typy CLR jsou typu jenom název typu, ale také sestavení.  To znamená se liší od určitého typu Z y.dll sestavení Z typu ze sestavení z.dll.  
  
## <a name="example"></a>Příklad  
 Tato ukázka obsahuje původní definici typu.  
  
```  
// C4691_a.cpp  
// compile with: /clr /LD /W1  
public ref class Original_Type {};  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka odkazuje C4691_a.dll a deklaruje pole typu Original_Type.  
  
```  
// C4691_b.cpp  
// compile with: /clr /LD  
#using "C4691_a.dll"  
public ref class Client {  
public:  
   Original_Type^ ot;  
};  
```  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C4691.  Všimněte si, tato ukázka obsahuje definici pro Original_Type a C4691a.dll neodkazuje.  
  
 Chcete-li vyřešit, odkaz na soubor metadat, která obsahuje původní definici typu a odeberte místní deklarace a definice.  
  
```  
// C4691_c.cpp  
// compile with: /clr /LD /W1  
// C4691 expected  
  
// Uncomment the following line to resolve.  
// #using "C4691_a.dll"  
#using "C4691_b.dll"  
  
// Delete the following line to resolve.  
ref class Original_Type;  
  
public ref class MyClass : Client {};  
```