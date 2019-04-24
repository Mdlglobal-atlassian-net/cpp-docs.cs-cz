---
title: Nastavení aplikace, průvodce MFC DLL
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.dll.appset
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
ms.openlocfilehash: f021f2023af839413306c1e3d56dc741749cf216
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152043"
---
# <a name="application-settings-mfc-dll-wizard"></a>Nastavení aplikace, průvodce MFC DLL

Tato stránka Průvodce MFC DLL slouží k návrhu a přidat základní funkce do nového projektu knihovny MFC DLL.

## <a name="dll-type"></a>Typ DLL

Vyberte typ knihovny DLL, kterou chcete vytvořit.

- **Běžné knihovny MFC DLL pomocí sdílenou knihovnu MFC DLL**

   Tuto možnost propojit váš program jako sdílenou knihovnu DLL knihovny MFC. Použití této možnosti nemůžete sdílet objekty MFC mezi knihovnou DLL a volající aplikace. Váš program provede volání do knihovny MFC v době běhu. Tato možnost snižuje požadavky na disku a paměti programu, pokud se skládá z více spustitelných souborů, které používají knihovnu MFC. Win32 a knihovny MFC programy mohou volat funkce v knihovně DLL. Musíte redistribuovat knihovnu MFC DLL s tímto typem projektu.

- **Běžné knihovny MFC DLL s knihovnou MFC staticky propojeny.**

   Tuto možnost propojení programu s knihovnou MFC staticky v okamžiku sestavení. Win32 a knihovny MFC programy mohou volat funkce v knihovně DLL. Při této možnosti dojde ke zvětšení program, není nutné znovu distribuovat knihovny DLL MFC s tímto typem projektu. Objekty knihovny MFC nelze sdílet mezi knihovnou DLL a volající aplikace.

- **MFC – rozšiřující knihovny DLL**

   Tuto možnost vyberte, pokud chcete program provádět volání do knihovny MFC v době běhu, a pokud budete chtít sdílet objekty MFC mezi knihovnou DLL a volající aplikace. Tato možnost snižuje požadavky na disku a paměti programu, pokud se skládá z více spustitelných souborů, které využívají knihovnu MFC. Pouze v aplikacích MFC lze volat funkce v knihovně DLL. Musíte redistribuovat knihovnu MFC DLL s tímto typem projektu.

## <a name="additional-features"></a>Další funkce

Vyberte, zda vaše knihovna DLL MFC by měl podporu automatizace, a zda má podporovat rozhraní Windows sockets.

- **Automatizace**

   Vyberte **automatizace** povolit program k manipulaci s objekty, které jsou implementovány v jiném programu. Výběr **automatizace** také poskytuje váš program jiným klientům automatizace. Zobrazit [automatizace](../../mfc/automation.md) Další informace.

- **Windows sockets**

   Tuto možnost použijte k označení, že vaše aplikace podporuje rozhraní Windows sockets. Windows sockets umožňuje psát programy, které komunikují v sítích TCP/IP.

   Pokud vaše knihovna MFC s Windows sockets – vytvoření podporu [CWinApp::InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) inicializuje podporu soketů a souboru hlaviček knihovny MFC StdAfx.h AfxSock.h.

## <a name="see-also"></a>Viz také:

[MFC DLL – průvodce knihovnou](../../mfc/reference/mfc-dll-wizard.md)<br/>
[Vytvoření projektu knihovny MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)
