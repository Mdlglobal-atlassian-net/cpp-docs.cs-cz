---
title: Zabalení (C + +/ CLI) | Dokumentace Microsoftu
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
ms.openlocfilehash: 4c513b0148e2553440e02f9b0d255a0d5750e2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372509"
---
# <a name="boxing-ccli"></a>Zabalení (C++/CLI)

Zabalení je proces převodu typu hodnoty na typ `object` nebo na libovolný typ rozhraní implementovaný typ hodnoty. Když common language runtime (CLR) pole typu hodnoty, obtéká hodnotu v `System.Object` a uloží ji na spravované haldě. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; Rozbalení je explicitní.

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)|Popisuje, jak explicitní žádost o zabalení u proměnné.|
|[Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Ukazuje, jak používat `gcnew` vytvořit zabalený typ hodnoty, které lze umístit do spravované, uvolnění paměti haldy.|
|[Postupy: Rozbalení](../dotnet/how-to-unbox.md)|Předvádí postup při rozbalení a třeba hodnotu změnit.|
|[Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)|Ukazuje, že standardní převod je kompilátor zvolí přes převod, který vyžaduje přetypování pomocí boxingu.|
|[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Článek nejvyšší úrovně pro .NET – programování v dokumentaci k Visual C++.|