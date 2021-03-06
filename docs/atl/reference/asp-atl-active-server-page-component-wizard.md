---
title: ASP, Průvodce stránky komponentami ATL Active Server
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.atl.asp.asp
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
ms.openlocfilehash: b88dffe2874d29918315af65c6ea093c24695f97
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503401"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Průvodce stránky komponentami ATL Active Server

Na této stránce průvodce komponenty ATL Active Server stránky můžete zadat volitelná nastavení pro zpracování informací a stavu související s vaší komponentě ASP.

- **Volitelné metody**

   Přidá metody volitelné ASP **OnStartPage** a **OnEndPage**, do objektu. Musí být vybraná tato možnost nastavit všechny vnitřní objekty Active Server Pages. Standardně je vybrána.

- **OnStartPage/OnEndPage**

   [Funkce OnStartPage](/previous-versions//ms691624\(v=vs.85\)) je volána při prvním pokusu skriptu pro přístup k objektu. **OnEndPage** se volá, když objekt dokončí zpracování skriptu.

- **Vnitřní objekt**

   Musíte vybrat **OnStartPage/OnEndPage** možnost nastavit všechny vnitřní objekty ASP.

|Možnost|Popis|
|------------|-----------------|
|**Požadavek**|Poskytuje přístup k Active Server Pages vnitřní **žádosti** objektu. Objekt požadavku se používá k předání požadavku HTTP.|
|**Odpověď**|Poskytuje přístup k Active Server Pages vnitřní **odpovědi** objektu. V reakci na žádost o objekt odpovědi odesílá informace do prohlížeče a zobrazí uživateli.|
|**Relace**|Poskytuje přístup k Active Server Pages vnitřní **relace** objektu. **Relace** objekt uchovává informace o aktuální uživatelské relace, včetně ukládání a načítání informací o stavu.|
|**Aplikace**|Poskytuje přístup k Active Server Pages vnitřní **aplikace** objektu. **Aplikace** objektu spravuje stav, který je sdílen mezi více objektů ASP.|
|**Server**|Poskytuje přístup k Active Server Pages vnitřní **Server** objektu. **Server** objekt umožňuje vytvářet další objekty, ASP.|

## <a name="see-also"></a>Viz také:

[Průvodce komponentami ATL Active Server Pages](../../atl/reference/atl-active-server-page-component-wizard.md)<br/>
[Komponenta knihovny ATL Active Server Page](../../atl/reference/adding-an-atl-active-server-page-component.md)
