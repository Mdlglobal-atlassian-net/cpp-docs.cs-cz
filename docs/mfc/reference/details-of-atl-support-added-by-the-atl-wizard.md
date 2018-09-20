---
title: Podrobnosti podpory knihovny ATL přidané Průvodcem knihovnou ATL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.atl.support
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: efa96037139e61e16b752b45617bb8a3c54be993
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442146"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Podrobnosti podpory knihovny ATL přidané průvodcem knihovnou ATL

Pokud jste [přidat podporu ATL do stávající spustitelný soubor knihovny MFC nebo knihovny DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual C++ provede následující změny v existujícím projektu knihovny MFC (v tomto příkladu se nazývá projektu `MFCEXE`):

- Jsou přidány dva nové soubory (souboru IDL a souboru .rgs použije k registraci serveru).

- V hlavní aplikaci záhlaví a implementaci souborech (Mfcexe.h a Mfcexe.cpp) nové třídy (odvozený od `CAtlMFCModule`) se přidá. Kromě novou třídu kód přidá `InitInstance` pro registraci. Kód je taky přidaný ke `ExitInstance` funkce pro zrušení objektu třídy. V souboru hlaviček, nakonec dva nové soubory hlaviček (Initguid.h a Mfcexe_i.c) jsou zahrnuty v souboru implementace, deklarace a inicializace nové identifikátory GUID pro `CAtlMFCModule`-odvozené třídy.

- K registraci serveru správně, se přidá záznam pro nový soubor .rgs do souboru prostředků projektu.

## <a name="notes-for-dll-projects"></a>Poznámky pro projekty knihovny DLL

Když přidat podporu ATL do projektu MFC DLL, zobrazí se několik rozdílů. Kód přidá `DLLRegisterServer` a `DLLUnregisterServer` funkce registrace a zrušení registrace knihovny DLL. Kód je taky přidaný ke [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) a [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Viz také

[Podpora knihovny ATL v projektu knihovny MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepisování virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Popisovače zpráv knihovny MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace strukturou třídy](../../ide/navigating-the-class-structure-visual-cpp.md)
