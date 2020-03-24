---
title: Zabalení (C++/CLI)
ms.date: 11/04/2016
ms.assetid: f4ee27a8-6a34-432d-b9ec-39285d513b23
ms.openlocfilehash: df0e220c4f744e78aa5bedce4f956b726f524ff4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208827"
---
# <a name="boxing-ccli"></a>Zabalení (C++/CLI)

Zabalení je proces převodu typu hodnoty na typ `object` nebo na jakýkoli typ rozhraní, který je implementován pomocí typu hodnoty. Když pole modulu CLR (Common Language Runtime) obsahuje typ hodnoty, zabalí hodnotu do `System.Object` a uloží ji na spravovanou haldu. Rozbalení extrahuje typ hodnoty z objektu. Zabalení je implicitní; rozbalení je explicitní.

## <a name="related-articles"></a>Související články

|Název|Popis|
|-----------|-----------------|
|[Postupy: Explicitní žádost o zabalení](../dotnet/how-to-explicitly-request-boxing.md)|Popisuje, jak explicitně požadovat zabalení u proměnné.|
|[Postupy: Vytváření typů hodnot pomocí výrazu gcnew s použitím implicitního zabalení](../dotnet/how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing.md)|Ukazuje, jak použít `gcnew` k vytvoření zabaleného typu hodnoty, který lze umístit na spravovanou haldu uvolňování paměti.|
|[Postupy: Rozbalení](../dotnet/how-to-unbox.md)|Ukazuje, jak Unbox a upravit hodnotu.|
|[Standardní převody a implicitní zabalení](../dotnet/standard-conversions-and-implicit-boxing.md)|Ukazuje, že kompilátor vybere standardní převod pomocí převodu, který vyžaduje zabalení.|
|[Programování pro .NET v jazyce C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)|Článek nejvyšší úrovně pro programování .NET v dokumentaci k vizuálu C++|
