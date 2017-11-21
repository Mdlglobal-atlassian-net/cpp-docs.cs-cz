---
title: "Postupy: zkompilování MFC a knihovny ATL kód pomocí - clr | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 77e28bcd53d5f497edbbff938f428322a9400fee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>Postupy: Kompilování kódu knihovny MFC a knihovny ATL s použitím přepínače /clr
Toto téma popisuje způsob kompilace existující MFC a knihovna ATL programů, pro které modul Common Language Runtime.  
  
### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>MFC DLL MFC, spustitelný soubor nebo regulární zkompilovat pomocí/CLR  
  
1.  Klikněte pravým tlačítkem na projekt v **Průzkumníku řešení** a pak klikněte na **vlastnosti**.  
  
2.  V **vlastnosti projektu** dialogové okno pole, rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. V pravém podokně v části **výchozí projekt**, nastavte **podpory Common Language Runtime** k **Podpora Common Language Runtime (/ clr)**.  
  
     V podokně stejné, ujistěte se, že **použití knihovny MFC** je nastaven na **použití knihovny MFC ve sdílené knihovně DLL**.  
  
3.  V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Ujistěte se, že **Debug Information Format** je nastaven na **Program Database /Zi** (ne **/ZI**).  
  
4.  Vyberte **generování kódu** uzlu. Nastavit **povolit minimální opětovné sestavení** k **ne (/ Gm –)**. Nastavte také **základní kontroluje Runtime** k **výchozí**.  
  
5.  V části **vlastnosti konfigurace**, vyberte **C/C++** a potom **generování kódu**. Ujistěte se, že **Runtime Library** je nastaven na hodnotu **Multi-threaded Debug DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)**.  
  
6.  V Stdafx.h přidejte následující řádek.  
  
    ```  
    #using <System.Windows.Forms.dll>  
    ```  
  
### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>Kompilace knihovnu DLL pomocí/CLR  
  
1.  Postupujte podle kroků v "A zkompilovat MFC spustitelný soubor nebo regulární knihovně MFC DLL pomocí/clr".  
  
2.  V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **předkompilovaných hlaviček**. Nastavit **vytvoření nebo použití předkompilovaných hlaviček** k **není použití předkompilovaných hlaviček**.  
  
     Jako alternativu v **Průzkumníku řešení**, klikněte pravým tlačítkem na Stdafx.cpp a pak klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavit **kompilovat s podporou modul Common Language Runtime** k **modul Common Language Runtime bez podpory**.  
  
3.  Pro soubor, který obsahuje DllMain a nic zavolá, v **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor a pak klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. V pravém podokně v části **výchozí projekt**, nastavte **kompilovat s podporou modul Common Language Runtime** k **modul Common Language Runtime bez podpory**.  
  
### <a name="to-compile-an-atl-executable-by-using-clr"></a>Zkompilovat spustitelný soubor knihovny ATL s použitím/CLR  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti**.  
  
2.  V **vlastnosti projektu** dialogové okno pole, rozbalte uzel vedle **vlastnosti konfigurace** a vyberte **Obecné**. V pravém podokně v části **výchozí projekt**, nastavte **podpory Common Language Runtime** k **Podpora Common Language Runtime (/ clr)**.  
  
3.  V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Ujistěte se, že **Debug Information Format** je nastaven na **Program Database /Zi** (ne **/ZI**).  
  
4.  Vyberte **generování kódu** uzlu. Nastavit **povolit minimální opětovné sestavení** k **ne (/ Gm –)**. Nastavte také **základní kontroluje Runtime** k **výchozí**.  
  
5.  V části **vlastnosti konfigurace**, vyberte **C/C++** a potom **generování kódu**. Ujistěte se, že **Runtime Library** je nastaven na hodnotu **Multi-threaded Debug DLL (/ MDd)** nebo **Multi-threaded DLL (/ MD)**.  
  
6.  Pro každý MIDL generovaný soubor (soubory C), klikněte pravým tlačítkem na soubor v **Průzkumníku řešení** a pak klikněte na **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavit **kompilovat s podporou modul Common Language Runtime** k **modul Common Language Runtime bez podpory**.  
  
### <a name="to-compile-an-atl-dll-by-using-clr"></a>Chcete-li zkompilovat ATL knihovny DLL pomocí/CLR  
  
1.  Postupujte podle kroků v části "ke kompilaci spustitelný soubor knihovny ATL s použitím/CLR".  
  
2.  V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **předkompilovaných hlaviček**. Nastavit **vytvoření nebo použití předkompilovaných hlaviček** k **není použití předkompilovaných hlaviček**.  
  
     Jako alternativu v **Průzkumníku řešení**, klikněte pravým tlačítkem na Stdafx.cpp a pak klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. Nastavit **kompilovat s podporou modul Common Language Runtime** k **modul Common Language Runtime bez podpory**.  
  
3.  Pro soubor, který obsahuje DllMain a nic zavolá, v **Průzkumníku řešení**, klikněte pravým tlačítkem na soubor a pak klikněte na tlačítko **vlastnosti**. V části **vlastnosti konfigurace**, rozbalte uzel vedle **C/C++** a vyberte **Obecné**. V pravém podokně v části **výchozí projekt**, nastavte **kompilovat s podporou modul Common Language Runtime** k **modul Common Language Runtime bez podpory**.  
  
## <a name="see-also"></a>Viz také  
 [Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)