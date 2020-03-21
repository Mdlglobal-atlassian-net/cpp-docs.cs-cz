---
title: Přidání komponenty ATL Active Server Page
ms.date: 05/09/2019
ms.assetid: 7be2204c-6e58-4099-8892-001b848c8987
ms.openlocfilehash: a84eeb20f047097e3dbb3c7f3bb5f5a12b069bcb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075304"
---
# <a name="adding-an-atl-active-server-page-component"></a>Přidání komponenty ATL Active Server Page

::: moniker range="vs-2019"

Průvodce komponentami ATL Active Server Pages není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

Chcete-li do projektu přidat objekt knihovny ATL (Active Template Library), projekt musí být vytvořen jako aplikace ATL COM nebo jako aplikace knihovny MFC, která obsahuje podporu knihovny ATL. Můžete použít [Průvodce projektem ATL](../../atl/reference/atl-project-wizard.md) k vytvoření aplikace ATL, můžete vybrat možnost **Přidat podporu knihovny ATL do knihovny MFC** z dialogového okna [Přidat třídu](../../ide/add-class-dialog-box.md) nebo můžete [Přidat objekt ATL do aplikace MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md) pro implementaci podpory knihovny ATL pro aplikaci MFC.

Komponenty Active Server stránky jsou součástí architektury Internetová informační služba, která poskytuje tyto pokročilé funkce pro vývoj webů:

- Komponenty ASP můžete vložit do stránek HTML a vytvořit tak dynamický obsah nezávislý na prohlížeči.

- Stránky ASP můžete použít k zajištění připojení databáze založené na standardech.

- Funkce pro zpracování chyb ASP můžete použít pro webové aplikace.

## <a name="to-add-an-atl-active-server-pages-component-to-your-project"></a>Přidání komponenty ATL Active Server Pages do projektu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na název projektu, do kterého chcete přidat komponentu ATL Active Server Pages.

1. V místní nabídce klikněte na tlačítko **Přidat**a poté klikněte na tlačítko **Přidat třídu**.

1. V dialogovém okně [Přidat třídu](../../ide/add-class-dialog-box.md) klikněte v podokně **šablony** na **Active Server komponenta stránky ATL**a potom klikněte na tlačítko **otevřít** . zobrazí se [Průvodce komponentami ATL Active Server Page](../../atl/reference/atl-active-server-page-component-wizard.md).

::: moniker-end

## <a name="see-also"></a>Viz také

[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Přidání nového rozhraní projektu ATL](../../atl/reference/adding-a-new-interface-in-an-atl-project.md)<br/>
[Přidání bodů připojení objektu](../../atl/adding-connection-points-to-an-object.md)<br/>
[Přidání metody](../../ide/adding-a-method-visual-cpp.md)<br/>
[MFC – třída](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání generické třídy jazyka C++](../../ide/adding-a-generic-cpp-class.md)
