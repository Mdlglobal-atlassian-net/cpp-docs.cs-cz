---
title: ASP, Průvodce stránky komponentami ATL Active Server | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.asp.asp
dev_langs:
- C++
helpviewer_keywords:
- ATL Active Server Page Component Wizard, ASP
ms.assetid: 4d8cafd6-5e12-4461-8911-29288896af3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 63f945f90f6a862a3b16cd3dcc41859b0c21b984
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761940"
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Průvodce stránky komponentami ATL Active Server

Na této stránce průvodce komponenty ATL Active Server stránky můžete zadat volitelná nastavení pro zpracování informací a stavu související s vaší komponentě ASP.

**Volitelné metody**  
Přidá metody volitelné ASP **OnStartPage** a **OnEndPage**, do objektu. Musí být vybraná tato možnost nastavit všechny vnitřní objekty Active Server Pages. Standardně je vybrána.

- **Funkce OnStartPage/OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) je volána při prvním pokusu skriptu pro přístup k objektu. **OnEndPage** se volá, když objekt dokončí zpracování skriptu.

**Vnitřní objekt**  
Musíte vybrat **OnStartPage/OnEndPage** možnost nastavit všechny vnitřní objekty ASP.

|Možnost|Popis|
|------------|-----------------|
|**Požadavek**|Poskytuje přístup k Active Server Pages vnitřní **žádosti** objektu. Objekt požadavku se používá k předání požadavku HTTP.|
|**Odpověď**|Poskytuje přístup k Active Server Pages vnitřní **odpovědi** objektu. V reakci na žádost o objekt odpovědi odesílá informace do prohlížeče a zobrazí uživateli.|
|**Relace**|Poskytuje přístup k Active Server Pages vnitřní **relace** objektu. **Relace** objekt uchovává informace o aktuální uživatelské relace, včetně ukládání a načítání informací o stavu.|
|**Aplikace**|Poskytuje přístup k Active Server Pages vnitřní **aplikace** objektu. **Aplikace** objektu spravuje stav, který je sdílen mezi více objektů ASP.|
|**Server**|Poskytuje přístup k Active Server Pages vnitřní **Server** objektu. **Server** objekt umožňuje vytvářet další objekty, ASP.|

## <a name="see-also"></a>Viz také

[Průvodce komponentami stránka ATL Active Server](../../atl/reference/atl-active-server-page-component-wizard.md)   
[Komponenta knihovny ATL Active Server Page](../../atl/reference/adding-an-atl-active-server-page-component.md)

