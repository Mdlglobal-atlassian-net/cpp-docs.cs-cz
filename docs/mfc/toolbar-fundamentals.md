---
title: Principy panelů nástrojů | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RT_TOOLBAR
dev_langs:
- C++
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fcb63ade0d1f2ad179448f448a10d88b71b91037
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383971"
---
# <a name="toolbar-fundamentals"></a>Principy panelů nástrojů
Tento článek popisuje základní implementace MFC, která umožňuje přidat výchozí panel nástrojů k vaší aplikaci výběrem možnosti v Průvodci aplikací. Obsahuje následující témata:  
  
-   [Možnosti nástrojů – Průvodce aplikací](#_core_the_appwizard_toolbar_option)  
  
-   [Panelu nástrojů v kódu](#_core_the_toolbar_in_code)  
  
-   [Úpravy prostředek panelu nástrojů](#_core_editing_the_toolbar_resource)  
  
-   [Více panelů nástrojů](#_core_multiple_toolbars)  
  
##  <a name="_core_the_appwizard_toolbar_option"></a> Možnost aplikace Průvodce panelu nástrojů  
 Chcete-li získat jeden panel nástrojů s výchozích tlačítek, vyberte možnost Standardní ukotvení panelu nástrojů na stránce s názvem bez přípony funkce uživatelského rozhraní. Tento postup přidá kódu do vaší aplikace který:  
  
-   Vytvoří objekt panelu nástrojů.  
  
-   Spravuje panelu nástrojů, včetně jeho schopnost ukotvení nebo float.  
  
##  <a name="_core_the_toolbar_in_code"></a> Panelu nástrojů v kódu  
 Panel nástrojů je [ctoolbar –](../mfc/reference/ctoolbar-class.md) objekt deklarován jako datový člen vaší aplikace **CMainFrame** třídy. Jinými slovy je objekt nástrojů vložený objekt hlavního rámce okna. To znamená, že MFC vytvoří panelu nástrojů při vytvoří okně s rámečkem a zničí panelu nástrojů, když ho zničí rámce okna. Následující prohlášení třídu pro více aplikací rozhraní (MDI) dokumentu ukazuje datových členů pro embedded panelu nástrojů a embedded stavový řádek. Také ukazuje přepis metody `OnCreate` – členská funkce.  
  
 [!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]  
  
 Dojde k vytvoření panelu nástrojů v **CMainFrame::OnCreate**. MFC volání [OnCreate](../mfc/reference/cwnd-class.md#oncreate) po vytvoření okna pro rámečku, ale předtím, než se zobrazí. Výchozí hodnota `OnCreate` , vygeneruje průvodce aplikací nemá následující úlohy nástrojů:  
  
1.  Volání `CToolBar` objektu [vytvořit](../mfc/reference/ctoolbar-class.md#create) – členská funkce pro vytvoření základní [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) objektu.  
  
2.  Volání [loadtoolbar –](../mfc/reference/ctoolbar-class.md#loadtoolbar) načíst informace o prostředcích panelu nástrojů.  
  
3.  Volání funkce povolit ukotvení, číslo s plovoucí čárkou a popisy. Podrobnosti o těchto volání, najdete v článku [stabilní umístění a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md).  
  
> [!NOTE]
>  Ukázka MFC Obecné [DOCKTOOL](../visual-cpp-samples.md) zahrnuje ilustrace staré a nové panely nástrojů rozhraní MFC. Panely nástrojů, které používají **COldToolbar** vyžadují volání v kroku 2 `LoadBitmap` (místo `LoadToolBar`) a `SetButtons`. Nových panelů nástrojů vyžadují volání `LoadToolBar`.  
  
 Ukotvení, číslo s plovoucí čárkou a nástroj tipy volání jsou volitelné. Můžete odebrat tyto řádky z `OnCreate` Pokud dáváte přednost. Výsledkem je zbývající pevné, nelze float nebo redock a nelze zobrazit popisy tlačítek panelu nástrojů.  
  
##  <a name="_core_editing_the_toolbar_resource"></a> Úpravy prostředek panelu nástrojů  
 Výchozí panel nástrojů získáte pomocí Průvodce aplikací je založena na **rt_toolbar –** vlastní prostředek, zavedená v prostředí MFC verze 4.0. Můžete upravit tento prostředek s [editor panelu nástrojů](../windows/toolbar-editor.md). Editor umožňuje snadno přidat, odstranit a změna uspořádání tlačítek. Obsahuje grafický editor pro tlačítka, který je velmi podobný editor obecné grafiky v jazyce Visual C++. Pokud jste upravili panely nástrojů v předchozích verzích Visual C++, najdete v ní úlohu mnohem snazší teď.  
  
 Tlačítka panelu nástrojů připojit k příkazu, dáváte tlačítko ID příkazu, například `ID_MYCOMMAND`. Zadejte ID příkazu, který na stránce vlastností tlačítka v editoru panelu nástrojů. Pak vytvořte obslužnou rutinu pro příkaz (viz [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md) Další informace).  
  
 Nové [ctoolbar –](../mfc/reference/ctoolbar-class.md) členské funkce pracovat **rt_toolbar –** prostředků. [Loadtoolbar –](../mfc/reference/ctoolbar-class.md#loadtoolbar) nyní probíhá z [loadbitmap –](../mfc/reference/ctoolbar-class.md#loadbitmap) načíst rastrového obrázku panelu nástrojů tlačítko imagí, a [setbuttons –](../mfc/reference/ctoolbar-class.md#setbuttons) nastavit styly tlačítek a připojit tlačítka s obrázky rastrového obrázku.  
  
 Podrobnosti o použití editoru panelu nástrojů najdete v tématu [Editor panelu nástrojů](../windows/toolbar-editor.md).  
  
##  <a name="_core_multiple_toolbars"></a> Více panelů nástrojů  
 Průvodce aplikací poskytuje jedno panelu nástrojů. Pokud potřebujete více než jeden panelu nástrojů v aplikaci, můžete model kódu pro další panely nástrojů na základě vygenerované Průvodcem kódu pro výchozí panel nástrojů.  
  
 Pokud chcete zobrazit panel nástrojů v důsledku příkaz, musíte:  
  
-   Vytvořte nový prostředek panelu nástrojů s panelu nástrojů editoru a načíst v `OnCreate` s [loadtoolbar –](../mfc/reference/ctoolbar-class.md#loadtoolbar) – členská funkce.  
  
-   Vložit nový [ctoolbar –](../mfc/reference/ctoolbar-class.md) objekt ve třídě hlavního rámce okna.  
  
-   Zkontrolujte odpovídající funkce volá v `OnCreate` ukotvení nebo float panelu nástrojů, nastavte jeho styly a tak dále.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o  
  
-   [Implementace panelu nástrojů v prostředí MFC (Přehled informací na panely nástrojů)](../mfc/mfc-toolbar-implementation.md)  
  
-   [Ukotvitelné a plovoucí panely nástrojů](../mfc/docking-and-floating-toolbars.md)  
  
-   [Popisy tlačítek panelu nástrojů](../mfc/toolbar-tool-tips.md)  
  
-   [Ctoolbar –](../mfc/reference/ctoolbar-class.md) a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) třídy  
  
-   [Práce s ovládacím prvkem panel nástrojů](../mfc/working-with-the-toolbar-control.md)  
  
-   [Použití starých panelů nástrojů](../mfc/using-your-old-toolbars.md)  
  
## <a name="see-also"></a>Viz také  
 [Implementace panelu nástrojů v prostředí MFC](../mfc/mfc-toolbar-implementation.md)

