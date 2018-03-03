---
title: "Průvodce ovládacím prvkem ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding controls
- controls [ATL], adding to projects
- ATL Control Wizard
ms.assetid: 991f8e72-ffbc-4382-a4ce-e255acfba5b6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9167153c2b827e1bc2597e830e9b3c82ee31b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-control-wizard"></a>Průvodce ovládacím prvkem knihovny ATL
Vloží do projektu knihovny ATL (nebo projektu knihovny MFC s podpory knihovny ATL) ovládacího prvku knihovny ATL. Tento průvodce vám pomůže vložit tři typy ovládacích prvků:  
  
-   Standardního ovládacího prvku  
  
-   Složeného ovládacího prvku  
  
-   Ovládací prvek DHTML  
  
 Kromě toho můžete zadat minimální ovládací prvek, odebrání rozhraní z [rozhraní](../../atl/reference/interfaces-atl-control-wizard.md) seznamu, které jsou k dispozici jako výchozí pro ovládací prvky otevřete ve většině kontejnerů. Můžete nastavit rozhraní chcete podporován u ovládacího prvku **rozhraní** stránce průvodce.  
  
## <a name="remarks"></a>Poznámky  
 Registrace skript vytvořený tímto průvodcem bude registrovat jeho komponenty COM HKEY_CURRENT_USER namísto HKEY_LOCAL_MACHINE. Chcete-li toto chování změnit, nastavte **zaregistrovat součást pro všechny uživatele** možnost ATL průvodce.  
  
## <a name="names"></a>Názvy  
 Zadejte názvy objektů, rozhraní a třídy, který se má přidat do projektu. S výjimkou **krátký název**, nezávisle na nástroji lze změnit všechna ostatní pole. Pokud změníte text pro **krátký název**, změny se projeví v názvech všechna ostatní pole na této stránce. Pokud změníte **třída typu Coclass** název v oddílu modelu COM, změna se odrazí v **typ** pole, ale **rozhraní** název a **ProgID** provést nelze změnit. Toto chování je navržená tak, aby bylo možné všechny názvy snadno identifikovat jako vývoje ovládacího prvku.  
  
> [!NOTE]
>  **Třída typu coclass** upravovat na pouze neoznačené atributy ovládací prvky. Pokud váš projekt s atributy, nelze upravovat **třída typu Coclass**.  
  
### <a name="c"></a>C++  
 Poskytuje informace o třídě C++ vytvořené implementovat objekt.  
  
 **Krátký název**  
 Nastaví zkrácený název objektu. Určuje název, který zadáte, třídy a **třída typu Coclass** názvy souboru (. CPP a. H) názvy, název rozhraní a **typ** názvy, pokud nezměníte tato pole samostatně.  
  
 **– Třída**  
 Nastaví název třídy, která implementuje objekt. Tento název je založen na název, který zadáte v **krátký název**, předcházet "C", typická předpona pro název třídy.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro nový objekt třídy. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložení názvu souboru do umístění podle vaší volby nebo připojit k existující soubor deklaraci třídy. Pokud vyberete existující soubor, průvodce jej neuloží do vybraného umístění dokud klikněte na tlačítko **Dokončit**.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být deklaraci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **souboru**  
 Nastaví název souboru implementace pro nový objekt třídu. Ve výchozím nastavení, tento název je založen na název, který zadáte v **krátký název**. Klikněte na tlačítko se třemi tečkami uložíte soubor do umístění podle vaší volby. Soubor se neuloží do vybraného umístění, dokud nekliknete na tlačítko **Dokončit** v průvodci.  
  
 Průvodce nepřepisuje soubor. Pokud vyberete název existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k označení, zda by měl být implementaci třídy přiložit k obsahu souboru. Klikněte na tlačítko **Ano** pro připojení k souboru; klikněte na tlačítko **ne** se vraťte do průvodce a zadejte jiný název souboru.  
  
 **S atributy**  
 Označuje, zda objekt používá atributy. Při přidávání objektu do projektu knihovny ATL, tato možnost je vybrané a nelze ji změnit. To znamená můžete přidat pouze objekty s atributy do projektu vytvořeného s podporou atribut.  
  
 Objekt s atributy můžete přidat pouze do projektu knihovny ATL, který používá atributy. Pokud vyberete tuto možnost pro projekt ATL, který nemá atribut podporovat, Průvodce zobrazí výzvu k určení, zda chcete přidat podporu atributů do projektu.  
  
 Ve výchozím nastavení, všechny objekty, přidejte po nastavení této možnosti jsou označeny jako s atributy (je zaškrtnuté políčko). Toto políčko Přidat objekt, který nepoužívá atributy.  
  
 V tématu [nastavení aplikace, Průvodce projektem ATL](../../atl/reference/application-settings-atl-project-wizard.md) a [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.  
  
### <a name="com"></a>Model COM  
 Poskytuje informace o funkci COM pro objekt.  
  
 **Třída typu coclass**  
 Nastaví název třídy komponenta, která obsahuje seznam podporovaných objektem rozhraní.  
  
> [!NOTE]
>  Pokud vytváříte váš projekt pomocí atributů, nebo pokud jste uvedli na této stránce průvodce, že ovládací prvek používá atributy, tuto možnost nelze změnit, protože knihovna ATL nezahrnuje **třída typu coclass** atribut.  
  
 **Rozhraní**  
 Nastaví název rozhraní pro objekt. Ve výchozím nastavení je před název rozhraní, která se zobrazí s "I".  
  
 **Typ**  
 Nastaví popis objektu, který se zobrazí v registru  
  
 **ProgID**  
 Nastaví název, který můžete použít kontejnery místo CLSID objektu. Toto pole není vyplněné automaticky. Pokud toto pole není ručně naplněn, nemusí být k dispozici pro další nástroje ovládacího prvku. Například ovládací prvky ActiveX, které jsou generovány bez `ProgID` nejsou k dispozici v **vložit ovládací prvek ActiveX** dialogové okno. Další informace o dialogovém okně najdete v tématu [Insert Dialog Box ovládací prvek ActiveX](../../windows/insert-activex-control-dialog-box.md).  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek ATL](../../atl/reference/adding-an-atl-control.md)   
 [Přidání funkcí do složeného ovládacího prvku](../../atl/adding-functionality-to-the-composite-control.md)   
 [Základy ATL – objekty COM](../../atl/fundamentals-of-atl-com-objects.md)

