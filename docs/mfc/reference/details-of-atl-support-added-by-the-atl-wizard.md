---
title: "Podrobnosti podpory knihovny ATL přidané Průvodcem knihovnou ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.atl.support
dev_langs: C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 49f17f1d5dd850034a802103ebd9208dc9bf8e87
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Podrobnosti podpory knihovny ATL přidané průvodcem knihovnou ATL
Pokud jste [přidání podpory knihovny ATL do stávající spustitelný soubor knihovny MFC nebo knihovny DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ provede následující změny v existující projektu knihovny MFC (v tomto příkladu se nazývá projektu `MFCEXE`):  
  
-   Se přidají dva nové soubory (souboru IDL a soubor .rgs, který se používá k registraci serveru).  
  
-   V hlavní aplikaci hlavičku a implementace souborech (Mfcexe.h a Mfcexe.cpp) novou třídu (odvozený z **CAtlMFCModule**) je přidána. Kromě, nová třída kód je přidán do `InitInstance` pro registraci. Kód je také přidán do `ExitInstance` funkce pro odvolání objektu třídy. V záhlaví souboru, nakonec dva nové soubory hlavičky (Initguid.h a Mfcexe_i.c) jsou zahrnuty v souboru implementace deklarace a inicializace nové identifikátory GUID pro **CAtlMFCModule**-odvozené třídy.  
  
-   Registrace serveru správně, je záznam pro nové souboru do souboru prostředků projektu.  
  
## <a name="notes-for-dll-projects"></a>Poznámky pro projekty knihovny DLL  
 Při přidání podpory knihovny ATL do projektu MFC DLL, zobrazí se některé rozdíly. Kód je přidán do **DLLRegisterServer** a **DLLUnregisterServer** funkce pro registraci a zrušení registrace knihovny DLL. Kód je taky přidaný ke [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) a [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).  
  
## <a name="see-also"></a>Viz také  
 [Podpora knihovny ATL v projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)   
 [Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)   
 [Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Popisovač zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
