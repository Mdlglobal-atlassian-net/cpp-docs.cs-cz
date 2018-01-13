---
title: "Stránka průvodce vlastností knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.ppg.overview
dev_langs: C++
helpviewer_keywords:
- ATL projects, adding property pages
- ATL Property Page Wizard
ms.assetid: 6113e325-facd-4f68-b491-144d75209922
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f97b4fcc84f9099ca7017eabd7ae5ead62cfe63
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-property-page-wizard"></a>Stránka průvodce vlastností knihovny ATL
Tento průvodce [přidá stránky vlastností do projektu knihovny ATL](../../atl/reference/adding-an-atl-property-page.md) nebo do projektu MFC s podpory knihovny ATL. Stránku vlastností knihovny ATL poskytuje uživatelské rozhraní pro nastavení vlastností (nebo volání metody) jeden nebo více objektů COM.  
  
## <a name="remarks"></a>Poznámky  
 Počínaje verzí Visual Studio 2008, registrace skript vytvořený tímto průvodcem bude registrovat jeho komponenty COM v **HKEY_CURRENT_USER** místo **HKEY_LOCAL_MACHINE**. Chcete-li toto chování změnit, nastavte **zaregistrovat součást pro všechny uživatele** možnost ATL průvodce.  
  
## <a name="names"></a>Názvy  
 Zadejte názvy objektů, rozhraní a třídy, který se má přidat do projektu. S výjimkou **krátký název**, všechny ostatní pole můžete upravovat nezávisle. Pokud změníte text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **třída typu Coclass** název v oddílu modelu COM, změna se odrazí v **typ** a **ProgID** polí. Toto chování je navržená tak, aby bylo možné všechny názvy snadno identifikovat jako vývoje stránky vlastností.  
  
> [!NOTE]
>  **Třída typu coclass** upravovat pouze neoznačené atributy projektů. Pokud váš projekt s atributy, nelze upravovat **třída typu Coclass**.  
  
### <a name="c"></a>C++  
 Poskytuje informace o třídě C++ vytvořené implementovat objekt.  
  
|||  
|-|-|  
|Termín|Definice|  
|**Krátký název**|Nastaví zkrácený název objektu. Určuje název, který zadáte, třídy a **třída typu Coclass** názvy souboru (**sada** a **.h**) názvy, **typ** název a  **ProgID**, pokud nezměníte tato pole jednotlivě.|  
|**soubor h**|Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud vyberete existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit** v průvodci.<br /><br /> Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.|  
|**– Třída**|Nastaví název třídy, která implementuje objekt. Tento název je založen na název, který zadáte v **krátký název**, předcházet "C", typická předpona pro název třídy.|  
|**souboru**|Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.<br /><br /> Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.|  
|**S atributy**|Označuje, zda objekt používá atributy. Pokud přidáváte objekt do projektu knihovny ATL, je vybraná tato možnost a nelze ji změnit, to znamená, můžete přidat pouze s atributy objektů do projektu vytvořeného s podporou atribut.<br /><br /> Objekt s atributy můžete přidat pouze do projektu knihovny ATL, který používá atributy. Pokud vyberete tuto možnost pro projekt ATL, který nemá atribut podporovat, Průvodce zobrazí výzvu k určení, zda chcete přidat podporu atributů do projektu.<br /><br /> Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s atributy (je zaškrtnuté políčko). Toto políčko Přidat objekt, který nepoužívá atributy.<br /><br /> V tématu [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.|  
  
### <a name="com"></a>Model COM  
 Poskytuje informace o funkci COM pro objekt.  
  
 **Třída typu coclass**  
 Nastaví název třídy komponenta, která obsahuje seznam podporovaných objektem rozhraní.  
  
> [!NOTE]
>  Pokud vytváříte váš projekt pomocí atributů, nebo pokud jste uvedli na této stránce průvodce, že stránka vlastností používá atributy, tuto možnost nelze změnit, protože knihovna ATL nezahrnuje `coclass` atribut.  
  
 **Typ**  
 Nastaví popis objektu, který se zobrazí v registru  
  
 **ProgID**  
 Nastaví název, který můžete použít kontejnery místo CLSID objektu.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti Průvodce stránky vlastností knihovny ATL](../../atl/reference/options-atl-property-page-wizard.md)   
 [Řetězce, Průvodce stránky vlastností knihovny ATL](../../atl/reference/strings-atl-property-page-wizard.md)   
 [Příklad: Implementace stránky vlastností](../../atl/example-implementing-a-property-page.md)

