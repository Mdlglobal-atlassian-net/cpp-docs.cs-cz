---
title: ASP, Průvodce komponentou stránky ASP ATL | Microsoft Docs
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
ms.openlocfilehash: dfe27a64a2086f08c5a29e2961d069771fdbc4e6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="asp-atl-active-server-page-component-wizard"></a>ASP, Průvodce komponentou stránky ASP knihovny ATL
Na této stránce Průvodce komponentou ATL Active Server stránky a zadejte volitelné nastavení pro zpracování informací a stavu související s příslušné součásti ASP.  
  
 **Volitelné metody**  
 Přidá volitelné metody ASP **OnStartPage** a **OnEndPage**, do objektu. Tuto možnost musíte vybrat nastavit vnitřní objekty stránek Active Server Pages. Standardně je vybraná.  
  
-   **OnStartPage nebo OnEndPage** [OnStartPage](https://msdn.microsoft.com/library/ms691624.aspx) je volána při prvním pokusu skriptu pro přístup k objektu. **OnEndPage** je volána, když objekt dokončí zpracování skriptu.  
  
 **Vnitřní objekt**  
 Je nutné vybrat **OnStartPage nebo OnEndPage** možnost nastavení ASP vnitřních objektů.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Požadavek**|Poskytuje přístup k Active Server Pages vnitřní **požadavku** objektu. Objekt požadavku slouží k předání požadavku HTTP.|  
|**Odpověď**|Poskytuje přístup k Active Server Pages vnitřní **odpovědi** objektu. V odpovědi na žádost o objekt odpovědi odesílá informace do prohlížeče, abyste zobrazit uživateli.|  
|**Relace**|Poskytuje přístup k Active Server Pages vnitřní **relace** objektu. **Relace** objekt uchovává informace o aktuální uživatelskou relaci, včetně ukládání a načítání informací o stavu.|  
|**Aplikace**|Poskytuje přístup k Active Server Pages vnitřní **aplikace** objektu. **Aplikace** objekt spravuje stav, který je sdílen mezi více objektů ASP.|  
|**Server**|Poskytuje přístup k Active Server Pages vnitřní **Server** objektu. **Server** objekt vám umožní vytvořit další objekty stránky ASP.|  
  
## <a name="see-also"></a>Viz také  
 [Průvodce komponentou stránky ASP knihovny ATL](../../atl/reference/atl-active-server-page-component-wizard.md)   
 [Komponenty ASP knihovny ATL](../../atl/reference/adding-an-atl-active-server-page-component.md)

