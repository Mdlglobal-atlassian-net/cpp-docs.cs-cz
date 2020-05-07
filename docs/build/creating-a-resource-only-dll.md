---
title: Vytvoření knihovny DLL obsahující pouze prostředky
description: Jak vytvořit knihovnu DLL pouze prostředků v aplikaci Visual Studio.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821340"
---
# <a name="creating-a-resource-only-dll"></a>Vytvoření knihovny DLL obsahující pouze prostředky

Knihovna DLL, která je pouze prostředky, je knihovna DLL, která neobsahuje žádné prostředky, jako jsou ikony, bitmapy, řetězce a dialogová okna. Použití knihovny DLL pouze prostředků je dobrým způsobem, jak sdílet stejnou sadu prostředků mezi více programy. Je také dobrým způsobem, jak poskytnout aplikaci s prostředky lokalizovanými pro více jazyků. Další informace naleznete v tématu [lokalizované prostředky v aplikacích MFC: satelitní knihovny DLL](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Vytvoření knihovny DLL s pouze prostředky

Chcete-li vytvořit knihovnu DLL pouze pro prostředky, vytvořte nový projekt Windows DLL (mimo MFC) a přidejte své prostředky do projektu:

::: moniker range="vs-2015"

1. V dialogovém okně **Nový projekt** vyberte **projekt Win32** . Zadejte název projektu a řešení a klikněte na **tlačítko OK**.

1. V **Průvodci aplikací Win32**vyberte **nastavení aplikace**. Vyberte **Typ aplikace** **knihovny DLL**. V části **Další možnosti**vyberte **prázdný projekt**. Kliknutím na tlačítko **Dokončit** vytvořte projekt.

1. Vytvořte nový skript prostředků, který obsahuje prostředky pro knihovnu DLL (například řetězec nebo nabídku). Uložte soubor `.rc`.

1. V nabídce **projekt** vyberte možnost **Přidat existující položku**a poté vložte nový `.rc` soubor do projektu.

1. Zadejte možnost linkeru [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY`zabraňuje linkeru v propojení odkazu s `_main` knihovnou DLL. Tato možnost je nutná k vytvoření knihovny DLL, která je jen pro prostředky.

1. Sestavení knihovny DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. V dialogovém okně **Nový projekt** vyberte **Průvodce desktopovou plochu systému Windows** a klikněte na tlačítko **Další**. Na stránce **Konfigurace nového projektu** zadejte název projektu a řešení a klikněte na tlačítko **vytvořit**.

1. V dialogovém okně **pracovní projekt systému Windows** vyberte **Typ aplikace** **dynamické knihovny**. V části **Další možnosti**vyberte **prázdný projekt**. Kliknutím na **tlačítko OK** vytvořte projekt.

1. Vytvořte nový skript prostředků, který obsahuje prostředky pro knihovnu DLL (například řetězec nebo nabídku). Uložte soubor `.rc`.

1. V nabídce **projekt** vyberte možnost **Přidat existující položku**a poté vložte nový `.rc` soubor do projektu.

1. Zadejte možnost linkeru [/NOENTRY](reference/noentry-no-entry-point.md) . `/NOENTRY`zabraňuje linkeru v propojení odkazu s `_main` knihovnou DLL. Tato možnost je nutná k vytvoření knihovny DLL, která je jen pro prostředky.

1. Sestavení knihovny DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Použít knihovnu DLL pouze pro prostředky

Aplikace, která používá knihovnu DLL pouze prostředků, by měla volat [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) nebo související funkce pro explicitní propojení s knihovnou DLL. Chcete-li získat přístup k prostředkům, zavolejte `FindResource` obecné `LoadResource`funkce a, které fungují na jakémkoli druhu prostředku. Nebo zavolejte jednu z následujících funkcí specifických pro prostředky:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

Aplikace by měla zavolat `FreeLibrary` po dokončení používání prostředků.

## <a name="see-also"></a>Viz také

[Práce se soubory prostředků](../windows/working-with-resource-files.md)\
[Vytváření knihoven DLL jazyka C/C++ v aplikaci Visual Studio](dlls-in-visual-cpp.md)
