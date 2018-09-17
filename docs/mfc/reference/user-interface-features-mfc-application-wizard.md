---
title: Funkce uživatelského rozhraní, Průvodce aplikací knihovny MFC | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.ui
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, user interface features
ms.assetid: 59e7b829-a665-42eb-be23-3f2a36eb2dad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29961e7b597683d3735203de9a47646b2a320469
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722550"
---
# <a name="user-interface-features-mfc-application-wizard"></a>Funkce uživatelského rozhraní, Průvodce aplikací MFC

Toto téma popisuje možnosti, které vám umožní určit vzhled vaší aplikace. Funkce uživatelského rozhraní dostupných pro váš projekt závisí na typu aplikace, které jste zadali v [typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC. Například pokud vytvoříte aplikaci rozhraní jednoho dokumentu, nelze přidat styly podřízených rámců.  
  
- **Styly hlavního rámce**

   Nastaví hlavní okno rámce aplikace funkcí.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Rámem**|Vytvoří okno, které velikosti ohraničení. Výchozí nastavení|  
   |**Minimalizovat pole**|V rámci hlavního okna obsahuje minimalizační pole. Výchozí nastavení|  
   |**Tlačítko maximalizace**|V rámci hlavního okna obsahuje maximalizační pole. Výchozí nastavení|  
   |**Minimalizovat**|Otevření okna hlavního rámce jako ikona.|  
   |**Maximalizované**|Otevře se okno hlavního rámce na plnou velikost zobrazení.|  
   |**Systémové nabídky**|Obsahuje systémovou nabídku v hlavní okno rámce. Výchozí nastavení|  
   |**O aplikaci**|Zahrnuje **o** pole pro aplikaci. Má uživatel přístup z aplikace toto políčko **pomáhají** nabídky. Výchozí nastavení a neměnný nevyberte **na bázi dialogu**v [typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md) stránky.<br /><br /> **Poznámka:** obvykle, není k dispozici možnost znamená, že průvodce se nedá použít možnost u projektu, zda není k dispozici položka zaškrtávací políčko zaškrtnuto nebo ne. V takovém případě vždy Průvodce přidá **o** pole do projektu, pokud nejprve zadat jako založená na dialogovém okně projektu a potom zrušte zaškrtnutí políčka.|  
   |**Počáteční stavového řádku**|Stavový řádek přidá do vaší aplikace. Stavový řádek obsahuje automatické ukazatele pro klávesy CAPS LOCK a NUM LOCK, SCROLL LOCK a řetězce zprávy řádek, který zobrazí nápovědu pro příkazy nabídek a panelů nástrojů tlačítka. Kliknutí na tuto možnost také přidá příkazy nabídky můžete zobrazit nebo skrýt stavový řádek. Aplikace má ve výchozím nastavení stavového řádku. Není k dispozici pro aplikace založené na dialogové okno typy.|  
   |**Rozdělit okno**|Poskytuje rozdělovač. Rozdělovač rozdělí hlavních zobrazení vaší aplikace. V aplikace (MDI interface) více dokumentů klienta okna podřízeného rámce MDI je okno s rozdělovačem. a v aplikaci rozhraní (SDI) jeden dokument a několik aplikačních nejvyšší úrovně dokumentu, okna hlavního rámce klienta je okno s rozdělovačem. Není k dispozici pro aplikace založené na dialogové okno typy.|  
  
- **Styly podřízených rámců**

   Určuje vzhled a počáteční stav podřízeného rámce ve vaší aplikaci. Jsou k dispozici pro aplikace MDI pouze styly podřízených rámců.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Minimalizace podřízeného prvku**|Určuje, zda podřízené okno má tlačítko Minimalizovat (standardně povoleno).|  
   |**Maximalizace podřízeného prvku**|Určuje, zda podřízené okno má tlačítko Maximalizovat (standardně povoleno).|  
   |**Podřízené maximalizované**|Určuje, zda podřízené okno zpočátku maximalizuje tak, že nastavíte cs.style příznak WS_MAXIMIZE v [PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow) členskou funkci `CChildFrame`.|  
  
- **Panely příkazů (nabídky nebo panelu nástrojů nebo pásu karet)**

   Určuje, zda vaše aplikace obsahuje nabídkami, panely nástrojů a/nebo pás karet. Není k dispozici pro aplikace založené na dialogové okno.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Použít klasickou nabídku**|Určuje, že vaše aplikace obsahuje classic-přetažitelného nabídky.|  
   |**Použít klasický ukotvení panelu nástrojů**|Standardní panel nástrojů Windows přidá do vaší aplikace. Panel nástrojů obsahuje tlačítka pro vytvoření nového dokumentu; otevírání a ukládání dokumentů; vyjímání, kopírování, vložení nebo tisk textu. a přechod do režimu nápovědy. Povolením této možnosti také přidá příkazy nabídky zobrazení nebo skrytí panelu nástrojů.|  
   |**Použít styl panelu nástrojů prohlížeče**|Přidá panel nástrojů Internet Explorer – vizuální styl pro vaši aplikaci.|  
   |**Použít řádek nabídek a panelů nástrojů**|Označuje, že vaše aplikace obsahuje přetažitelného nabídek a panelů nástrojů.|  
   |**Uživatelem definované nástrojů a obrázky**|Umožňuje uživateli přizpůsobovat panel nástrojů a obrázky panelu nástrojů za běhu.|  
   |**Chování individuální nabídky**|Určuje, zda nabídka obsahuje úplný seznam položek při otevření, nebo pokud obsahuje jenom příkazy, které uživatel používá nejčastěji.|  
   |**Použít pás karet**|Použije pásu karet Office 2007 jako svou aplikaci, ne řádku nabídek nebo na panelu nástrojů.|  
  
- **Název dialogového okna**

   Pro [CDialog – třída](../../mfc/reference/cdialog-class.md)– aplikace založené na pouze tento název se zobrazí v záhlaví dialogového okna. Chcete-li upravit toto pole, musíte nejprve vybrat **na bázi dialogu** v části **typ aplikace**. Další informace najdete v tématu [typ aplikace, Průvodce aplikací knihovny MFC](../../mfc/reference/application-type-mfc-application-wizard.md).  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

