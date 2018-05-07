---
title: Chyba linkerů Lnk1256 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- xml
- LNK1256
dev_langs:
- C++
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e4039dccb4dc8abd421b4622bbe928931f7f396
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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