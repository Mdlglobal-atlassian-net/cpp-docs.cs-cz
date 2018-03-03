---
title: "Zabalení (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e49c6f82099e6d7dbcfc47079d19228d7a91dc05
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="boxing-ccli"></a>Zabalení (C++/CLI)
Zabalení je proces převodu typu hodnoty na typ `object` nebo k libovolnému typu rozhraní, které je implementované typ hodnoty. Pokud modul CLR (CLR) oknech typ hodnoty, se zabalí hodnotu v `System.Object` a uloží je na spravované haldě. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; Rozbalení je explicitní.  
  
## <a name="related-articles"></a>Související články  
  
|Název|Popis|  
|-----------|-----------------|  
|[Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)|Popisuje, jak explicitní žádost o zabalení na proměnnou.|  
|[Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Ukazuje, jak používat `gcnew` vytvoření zabalené hodnoty typu, který se může v haldě spravovaná, uvolňování paměti.|  
|[Postupy: Rozbalení](../dotnet/how-to-unbox.md)|Ukazuje, jak unbox a upravte hodnotu.|  
|[Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)|Ukazuje, že je standardní převod zvolen kompilátorem přes převodu, která vyžaduje zabalení.|  
|[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Nejvyšší úrovně článku .NET – programování v jazyce Visual C++ dokumentaci.|