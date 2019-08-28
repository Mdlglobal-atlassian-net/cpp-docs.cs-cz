---
title: Podrobnosti podpory knihovny ATL přidané průvodcem knihovnou ATL
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108458"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Podrobnosti podpory knihovny ATL přidané průvodcem knihovnou ATL

::: moniker range=">=vs-2019"

Přidáte-li [podporu knihovny ATL do existujícího spustitelného souboru knihovny MFC nebo knihovny DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio přidá ve výchozím nastavení hlavičkový soubor s názvem `#include` *Framework. h* , který obsahuje direktivy preprocesoru a `#define` umožňuje použití ATL v projektu. Nepřidaly se žádné další soubory ani třídy, jak bylo provedeno v předchozích verzích sady Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Když [přidáte podporu knihovny ATL do existujícího spustitelného souboru knihovny MFC nebo knihovny DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), aplikace Visual Studio provede následující úpravy v existujícím projektu knihovny MFC (v tomto příkladu je `MFCEXE`projekt volán):

- Přidají se dva nové soubory (soubor. idl a soubor. rgs, který se používá k registraci serveru).

- V hlavní aplikační hlavičce a implementační soubory (Mfcexe. h a Mfcexe. cpp) je přidána nová třída (odvozená od `CAtlMFCModule`). Kromě nové třídy je kód přidán k `InitInstance` pro registraci. Kód je také přidán do `ExitInstance` funkce pro odvolání objektu třídy. V souboru hlaviček jsou nakonec do implementačního souboru zahrnuty dva nové hlavičkové soubory (Initguid. h a Mfcexe_i. c), které deklaruje a inicializuje nové identifikátory GUID pro třídu odvozenou `CAtlMFCModule`od třídy.

- Pro správné registraci serveru je do souboru prostředků projektu přidána položka nového souboru. rgs.

::: moniker-end

## <a name="notes-for-dll-projects"></a>Poznámky pro projekty knihoven DLL

Při přidání podpory knihovny ATL do projektu knihovny MFC se zobrazí některé rozdíly. Kód se přidá do `DLLRegisterServer` funkcí a `DLLUnregisterServer` pro registraci a zrušení registrace knihovny DLL. Kód je také přidán do [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) a [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Viz také:

[Podpora ATL v projektu MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání členské funkce](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Přidání členské proměnné](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Přepsání virtuální funkce](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Obslužná rutina zpráv MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Navigace ve struktuře třídy](../../ide/navigate-code-cpp.md)
