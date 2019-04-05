---
title: Práce se zdrojovými soubory (C++)
ms.date: 02/14/2019
helpviewer_keywords:
- resources [C++], about resources
- resources [C++], about resource files
- resource files [C++], about resource files
ms.assetid: 2699a539-b369-4b78-80f0-df03eb7b6780
ms.openlocfilehash: a08c7ecb153b790f06da386ac93d1f05f5981e61
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037727"
---
# <a name="working-with-resource-files"></a>Práce se zdrojovými soubory

> [!WARNING]
> Tato část se týká aplikací klasické pracovní plochy Windows napsaný v jazyce C++.
>
> Informace o prostředcích v aplikacích pro univerzální platformu Windows napsaný v jazyce C++, naleznete v tématu [definování prostředků aplikace](/windows/uwp/app-resources/), nebo o přidávání prostředků do C + +/ CLI (spravované) projekty, naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v Příručka pro vývojáře rozhraní .NET Framework.

Prostředky může skládat ze široké škály prvky, jako je:

- Prvky rozhraní, které poskytují informace o uživateli, jako je například bitmapy, ikony nebo kurzoru.
- Vlastní prostředky, které obsahují data a aplikace potřebuje.
- Verze zdroje, které jsou používány instalační program rozhraní API.
- Integrované prostředky nabídky a dialogové okno.

Můžete přidat nové prostředky do projektu a upravit tyto prostředky pomocí editoru odpovídající prostředek. Většina průvodců aplikace Visual C++ bude automaticky generovat soubor .rc pro váš projekt.

> [!NOTE]
> **Editory prostředků** a **zobrazení prostředků** nejsou k dispozici ve verzích Express.

Ruční přidání souborů prostředků do spravovaných projektů, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Tento článek obsahuje informace, jak přístup k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnosti.

Globalizace a lokalizace prostředků ve spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="in-this-section"></a>V tomto oddílu

[Zdrojové soubory](../windows/resource-files-visual-studio.md)<br/>
Popisuje soubory prostředků a jak se používají v aplikacích klasické pracovní plochy Windows. Obsahuje také odkazy na články, které popisují způsob použití souborů prostředků.

[Identifikátory prostředků (symbolů)](../windows/symbols-resource-identifiers.md)<br/>
Popisuje symboly a poskytuje informace o používání **symbolů prostředků** dialogové okno ke správě symbolů ve vašich projektech.

[Editory prostředků](../windows/resource-editors.md)<br/>
Popisuje editory prostředků k dispozici v sadě Visual Studio a typy prostředků, které můžete upravit každé editoru. Obsahuje také odkazy na podrobné informace o používání každý editor.

## <a name="related-sections"></a>Související oddíly

[Visual C++](../overview/visual-cpp-in-visual-studio.md)<br/>
Obsahuje odkazy na dokumentaci jazyka Visual C++.

[Kontaktujte nás](/visualstudio/ide/talk-to-us)<br/>
Obsahuje odkazy na informace o používání sady dokumentace, kontaktovat podporu produktů a použití funkce pro usnadnění přístupu.

## <a name="see-also"></a>Viz také:

[Desktopové aplikace Windows](../windows/windows-desktop-applications-cpp.md)<br/>
[Nabídky a ostatní prostředky](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)