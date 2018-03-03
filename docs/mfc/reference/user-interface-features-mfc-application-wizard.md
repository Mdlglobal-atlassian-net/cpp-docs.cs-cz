---
title: "Funkce uživatelského rozhraní, Průvodce aplikací knihovny MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5906cf607e09df536825eed88e7b1be59d8fdee2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-features-mfc-application-wizard"></a>Funkce uživatelského rozhraní, Průvodce aplikací MFC
Toto téma vysvětluje možnosti, které můžete použít k určení vzhledu vaší aplikace. Funkce uživatelského rozhraní k dispozici pro váš projekt závisí na typu aplikace, které jste zadali v [typu aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací MFC. Například pokud vytvoříte aplikaci rozhraní jedním dokumentem, nelze přidat styly podřízeného rámce.  
  
 **Styly hlavního rámce**  
 Nastaví funkce aplikace hlavního rámce okna.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Silný rámeček**|Vytvoří okno, které podporuje změnu velikosti ohraničení. Výchozí nastavení|  
|**Minimalizovat pole**|Zahrnuje minimalizace v hlavním okně rámce. Výchozí nastavení|  
|**Maximalizovat pole**|Zahrnuje maximalizace v hlavním okně rámce. Výchozí nastavení|  
|**Minimalizované**|Otevře okno rámce jako ikonu.|  
|**Maximalizovaný**|Otevře se hlavního rámce okno na plnou velikost zobrazení.|  
|**Nabídky systému**|Obsahuje systémovou nabídku v hlavním okně rámce. Výchozí nastavení|  
|**O pole**|Zahrnuje **o** pole pro aplikaci. Uživatel může k tomuto poli přístup z aplikace **pomoci** nabídky. Výchozí nastavení a neměnný, pokud nevyberete možnost **dialogové okno na základě**v [typu aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránky.<br /><br /> **Poznámka:** obvykle, není k dispozici možnost označuje, že v Průvodci se nevztahuje možnost projektu, zda je zaškrtnuto políčko u položky k dispozici nebo ne. V takovém případě vždy Průvodce přidá **o** pole do projektu, pokud nejprve zadat jako dialogové okno na základě projektu a potom zrušte zaškrtnutí políčka.|  
|**Počáteční stavového řádku**|Přidá stavového řádku do vaší aplikace. Stavový řádek obsahuje automatické ukazatele pro klávesy CAPS LOCK, NUM LOCK a SCROLL LOCK a řetězce zpráva řádek, který zobrazuje nápovědu pro příkazy nabídek a panelů nástrojů tlačítka. Kliknutím na tuto možnost také přidá příkazy nabídky zobrazí nebo skryje stavový řádek. Ve výchozím nastavení má aplikace stavový řádek. Není k dispozici pro aplikace založené na dialogové okno typy.|  
|**Rozdělení oken**|Poskytuje rozdělovač. Rozdělovač rozdělí hlavní zobrazení aplikace. V více aplikací rozhraní (MDI) dokumentu rámečku podřízeného MDI klienta není rozdělovače okně a v aplikaci jedním dokumentem (SDI rozhraní) a více nejvyšší úrovně dokumentu aplikace, se hlavního rámce okna klienta rozdělovače oken. Není k dispozici pro aplikace založené na dialogové okno typy.|  
  
 **Styly podřízeného rámce**  
 Určuje vzhled a počáteční stav podřízeného rámce v aplikaci. Styly podřízeného rámce jsou k dispozici pro aplikace MDI jenom.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Minimalizace podřízeného prvku**|Určuje, zda je podřízeného okna tlačítko Minimalizovat (povolené ve výchozím nastavení).|  
|**Maximalizace podřízeného**|Určuje, zda má podřízeného okna tlačítko Maximalizovat (povolené ve výchozím nastavení).|  
|**Maximalizovaný podřízený**|Určuje, zda je podřízeného okna původně maximalizovaný nastavením příznaku cs.style **WS_MAXIMIZE –** v [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) členské funkce `CChildFrame`.|  
  
 **Panely příkazů (nabídky nebo panelu nástrojů nebo pásu karet)**  
 Určuje, jestli vaše aplikace obsahuje nabídky, panely nástrojů nebo pásu karet. Není k dispozici pro aplikace založené na dialogové okno.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Použít classic nabídky**|Určuje, že vaše aplikace obsahuje classic, přetahovatelným nabídky.|  
|**Použít classic ukotvení panelu nástrojů**|Standardním panelu nástrojů systému Windows přidá do vaší aplikace. Panel nástrojů obsahuje tlačítka pro vytvoření nového dokumentu; otevření a uložení dokumentu souborů; vyjímání, kopírování, vložením nebo tisk textu. a přejít do režimu nápovědy. Povolením této možnosti také přidá příkazy nabídky k zobrazení nebo skrytí panelu nástrojů.|  
|**Použít styl panelu nástrojů prohlížeče**|Panelu nástrojů Internet Explorer-style přidá do vaší aplikace.|  
|**Použití řádku nabídek a panelů nástrojů**|Označuje, že vaše aplikace obsahuje přetahovatelným nabídek a panelů nástrojů.|  
|**Vlastní panely nástrojů a obrázků**|Umožňuje uživateli upravit panelu nástrojů a jeho obrázků za běhu.|  
|**Chování přizpůsobené nabídky**|Určuje, zda nabídka obsahuje úplný seznam položek při otevření nebo pokud obsahuje jenom příkazy, které uživatel používá nejčastěji.|  
|**Použít pásu karet**|Používá pásu karet Office 2007 jako svou aplikaci, ne na řádku nabídek nebo panelu nástrojů.|  
  
 **Název dialogového okna**  
 Pro [CDialog – třída](../../mfc/reference/cdialog-class.md)– na základě pouze aplikací, tento název se zobrazí v záhlaví dialogového okna. Chcete-li upravit toto pole, musíte nejdřív vybrat **založená na dialogovém okně** možnost v části **typ aplikace**. Další informace najdete v tématu [typu aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

