---
title: Zabalení (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: 3f756eaef59c24ca5b82c485bd8352dffe9fb1db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614497"
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