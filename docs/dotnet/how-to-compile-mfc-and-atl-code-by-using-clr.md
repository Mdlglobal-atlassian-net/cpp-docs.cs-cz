---
title: 'Postupy: Kompilace kódu MFC a ATL s použitím - clr'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
ms.openlocfilehash: 9a24e82787eb0fce8ff668843e73de9f2d05e1ad
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751606"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Postupy: Zkompilujte knihovnu MFC a ATL kód pomocí/CLR

Toto téma popisuje, jak kompilovat existující programy MFC a ATL cílit na modul Common Language Runtime.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>Chcete-li zkompilovat MFC spustitelný soubor nebo běžné knihovny MFC DLL pomocí/CLR

1. Klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a potom klikněte na tlačítko **vlastnosti**.

1. V **vlastnosti projektu** dialogového okna rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. V pravém podokně v části **výchozí nastavení projektu**, nastavte **Common Language Runtime support** k **Common Language Runtime Support (/ clr)**.

   V podokně stejné, ujistěte se, že **použít knihovnu MFC** je nastavena na **použít knihovnu MFC ve sdílené knihovně DLL**.

1. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Ujistěte se, že **formát informací o ladění** je nastavena na **databázi programu /Zi** (ne **/zi**).

1. Vyberte **generování kódu** uzlu. Nastavte **povolit minimální opětovné sestavení** k **ne (/ Gm-)**. Nastavit také **Basic Runtime Checks** k **výchozí**.

1. V části **vlastnosti konfigurace**vyberte **C/C++** a potom **generování kódu**. Ujistěte se, že **knihovny prostředí Runtime** je nastaven na hodnotu **Multi-threaded ladit knihovnu DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)**.

1. Ve Stdafx.h přidejte následující řádek.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Chcete-li zkompilovat rozšiřující knihovny DLL MFC pomocí/CLR

1. Postupujte podle kroků v "Ke kompilaci MFC spustitelný soubor nebo běžné knihovny MFC DLL pomocí/clr".

1. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **předkompilované hlavičky**. Nastavte **vytvoření a použití předkompilovaných hlaviček** k **bez použití předkompilovaných hlaviček**.

   Jako alternativu v **Průzkumníka řešení**Stdafx.cpp pravým tlačítkem myši a potom klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavte **kompilovat s podporou Common Language Runtime** k **ne Common Language Runtime support**.

1. Pro soubor, který obsahuje funkce DllMain a veškerých kódů, které volá, v **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor a potom klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. V pravém podokně v části **výchozí nastavení projektu**, nastavte **kompilovat s podporou Common Language Runtime** k **ne Common Language Runtime support**.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>Chcete-li zkompilovat spustitelný soubor knihovny ATL s použitím/CLR

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a potom klikněte na tlačítko **vlastnosti**.

1. V **vlastnosti projektu** dialogového okna rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. V pravém podokně v části **výchozí nastavení projektu**, nastavte **Common Language Runtime support** k **Common Language Runtime Support (/ clr)**.

1. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Ujistěte se, že **formát informací o ladění** je nastavena na **databázi programu /Zi** (ne **/zi**).

1. Vyberte **generování kódu** uzlu. Nastavte **povolit minimální opětovné sestavení** k **ne (/ Gm-)**. Nastavit také **Basic Runtime Checks** k **výchozí**.

1. V části **vlastnosti konfigurace**vyberte **C/C++** a potom **generování kódu**. Ujistěte se, že **knihovny prostředí Runtime** je nastaven na hodnotu **Multi-threaded ladit knihovnu DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)**.

1. Pro každý MIDL generovaný soubor (soubory jazyka C), klikněte pravým tlačítkem na soubor v **Průzkumníka řešení** a potom klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavte **kompilovat s podporou Common Language Runtime** k **ne Common Language Runtime support**.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>Chcete-li zkompilovat ATL DLL pomocí/CLR

1. Postupujte podle kroků v části "ke kompilaci spustitelný soubor knihovny ATL s použitím/CLR".

1. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **předkompilované hlavičky**. Nastavte **vytvoření a použití předkompilovaných hlaviček** k **bez použití předkompilovaných hlaviček**.

   Jako alternativu v **Průzkumníka řešení**Stdafx.cpp pravým tlačítkem myši a potom klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavte **kompilovat s podporou Common Language Runtime** k **ne Common Language Runtime support**.

1. Pro soubor, který obsahuje funkce DllMain a veškerých kódů, které volá, v **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor a potom klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. V pravém podokně v části **výchozí nastavení projektu**, nastavte **kompilovat s podporou Common Language Runtime** k **ne Common Language Runtime support**.

## <a name="see-also"></a>Viz také:

[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)
