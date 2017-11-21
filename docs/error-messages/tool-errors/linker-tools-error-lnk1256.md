---
title: "Chyba linkerů Lnk1256 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs: C++
helpviewer_keywords: LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5a7b024971c1e2e9c938ee6519772f59f333fb28
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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