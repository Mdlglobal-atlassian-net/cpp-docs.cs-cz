---
title: Průvodce ovládacím prvkem ActiveX knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.overview
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 45af43a98244e90f52075817fc9e17a905cbf065
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-control-wizard"></a>Průvodce ovládacím prvkem ActiveX v prostředí MFC
Ovládací prvek ActiveX je určitý typ [automatizační server](../../mfc/automation-servers.md); je znovu použitelné komponentní. Hostování ovládacího prvku ActiveX aplikace je [klienta automatizace](../../mfc/automation-clients.md) tohoto ovládacího prvku. Pokud je vaším cílem je vytvořit znovu použitelné komponentní, pomocí tohoto průvodce k vytvoření vlastního ovládacího prvku. V tématu [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md) Další informace.  
  
 Alternativně můžete vytvořit automation server MFC aplikace pomocí [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md).  
  
 Ovládací prvek ActiveX, který je vytvořen pomocí tohoto průvodce můžete mít uživatelské rozhraní, nebo může být skrytá. Můžete určit, tato možnost v [nastavení řízení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránku průvodce. Ovládací prvek časovače je příkladem ovládací prvek ActiveX, který chcete, aby byla neviditelná.  
  
 ActiveX – ovládací prvky můžete mít složité uživatelské rozhraní. Některé ovládací prvky může být jako zapouzdřené formuláře: jeden ovládací prvek obsahující mnoho polí se každý ovládacího prvku Windows v sobě. Objekt částí automaticky implementované jako ovládacího prvku ActiveX knihovny MFC mohou například představovat formuláře jako uživatelské rozhraní, přes který by mohl přečíst a upravit výrobní číslo, název součásti a další informace uživatele. V tématu [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md) Další informace.  
  
 Pokud potřebujete vytvořit kontejner pro objekty technologie ActiveX, přečtěte si téma [vytvoření kontejneru ovládacího prvku ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).  
  
 Výchozí program knihovny MFC zahrnuje C++ zdrojové (sada) soubory, soubory prostředků (RC) a soubor projektu (VCXPROJ). Kód, který vygenerovala v těchto souborech starter vychází MFC.  
  
 V následujícím seznamu ukázka uvádí úlohy a typy rozšíření pro ovládací prvek ActiveX:  
  
-   [Optimalizace ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-optimization.md)  
  
-   [Přidání uložených událostí do ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [Přidání vlastních událostí](../../mfc/mfc-activex-controls-adding-custom-events.md)  
  
-   [Přidání uložených metod](../../mfc/mfc-activex-controls-adding-stock-methods.md)  
  
-   [Přidání vlastních metod](../../mfc/mfc-activex-controls-adding-custom-methods.md)  
  
-   [Přidání uložených vlastností](../../mfc/mfc-activex-controls-adding-stock-properties.md)  
  
-   [Přidání vlastních vlastností](../../mfc/mfc-activex-controls-adding-custom-properties.md)  
  
-   [Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
## <a name="overview"></a>Přehled  
 Tato stránka průvodce popisuje aktuální nastavení aplikace pro projekt ovládacího prvku ActiveX knihovny MFC, kterou vytváříte. Ve výchozím nastavení Průvodce vytvoří projekt takto:  
  
-   Výchozí projekt generuje žádné licence nebo nápovědy spustitelné soubory. Tato výchozí nastavení můžete změnit na [nastavení aplikace](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) stránky. Pouze na této stránce Průvodce ovládacím prvkem ActiveX provedete výběr se projeví ve **přehled** stránky.  
  
-   Tento projekt zahrnuje ovládací prvek třídy a třídy stránky vlastností na základě názvu projektu. Názvy vašeho projektu a názvy souborů můžete upravit na [názvy ovládacích prvků](../../mfc/reference/control-names-mfc-activex-control-wizard.md) stránky.  
  
-   Ovládací prvek je založen na žádné existující ovládacího prvku systému Windows, aktivuje, když se zobrazí, má uživatelské rozhraní a zahrnuje **o** dialogové okno. Tato výchozí nastavení můžete změnit na [nastavení řízení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření a správa projektů Visual C++](../../ide/creating-and-managing-visual-cpp-projects.md)   
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)   
 [Koncepty](../../atl/active-template-library-atl-concepts.md)

