---
title: "Chyba linkerů Lnk1256 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bbbb14e4f4fdef63b58bdef5ecafcfe0b045f412
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk1256"></a>Chyba linkerů LNK1256
ALINK operace se nezdařila: důvod  
  
 Obvyklým důvodem LNK1256 je nesprávné číslo verze sestavení. Hodnota 65535 není povolena pro libovolnou část číslo verze sestavení. Verze sestavení platný rozsah hodnot je 0 - 65534.  
  
 LNK1256 může také dojít, pokud ALINK nelze nalézt kontejner s názvem klíče. Odstranit kontejner klíčů a přidejte ji znovu do silný název CSP pomocí [Sn.exe (nástroj silným názvem)](/dotnet/framework/tools/sn-exe-strong-name-tool).  
  
 Dalším důvodem pro LNK1256 je Neshoda verzí mezi linkeru a Alink.dll. Příčinou může být poškozená instalace Visual Studia. Použití **programy a funkce** v Ovládacích panelech opravy a nové instalace sady Visual Studio.  
  
 Následující ukázka generuje LNK1256:  
  
```  
// LNK1256.cpp  
// compile with: /clr /LD  
// LNK1256 expected  
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];  
public class CMyClass {  
public:  
   int value;  
};  
```