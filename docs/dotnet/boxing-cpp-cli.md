---
title: Zabalení (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3b9898b4a640d2f3aa4e38ceb621521ffb301fed
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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