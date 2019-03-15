---
title: Průvodce ovládacím prvkem ActiveX v prostředí MFC
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: cec4c3aa6aedfa7a1f8234c6cc2355970d453f56
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822675"
---
# <a name="mfc-activex-control-wizard"></a>Průvodce ovládacím prvkem ActiveX v prostředí MFC

Ovládací prvek ActiveX je konkrétní typ [automatizační server](../../mfc/automation-servers.md); je opětovně použitelnou komponentu. Aplikace hostující ovládací prvek ActiveX je [klient automatizace](../../mfc/automation-clients.md) ovládacího prvku. Pokud je vaším cílem je vytvořit opětovně použitelnou komponentu, pomocí tohoto průvodce k vytvoření ovládacího prvku. Zobrazit [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md) Další informace.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](../activex-controls.md).

Alternativně můžete vytvořit automatizační server knihovny MFC aplikace s využitím [Průvodce aplikací knihovny MFC](../../mfc/reference/mfc-application-wizard.md).

Ovládací prvek ActiveX vytvořené pomocí tohoto průvodce můžete mít uživatelské rozhraní, nebo může být viditelná. Můžete určit tuto možnost v [nastavení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránku průvodce. Ovládací prvek časovače je příkladem ovládacího prvku ActiveX, který chcete, aby byla neviditelná.

Ovládací prvky ActiveX můžete mít složitý uživatelské rozhraní. Mohou být některé ovládací prvky jako zapouzdřený objekt formuláře: jeden ovládací prvek obsahující mnoho polí se každý ovládací prvek Windows v sama o sobě. Objekt částí automaticky implementovaná jako ovládací prvek ActiveX knihovny MFC například mohou představovat formuláře jako uživatelské rozhraní, přes který by mohl přečíst a upravit číslo součásti, názvu součásti a další informace uživatele. Zobrazit [ovládací prvky MFC ActiveX](../../mfc/mfc-activex-controls.md) Další informace.

Pokud je potřeba vytvořit kontejner pro objekty ActiveX, přečtěte si téma [vytvoření kontejneru ovládacího prvku ActiveX](../../mfc/reference/creating-an-mfc-activex-control-container.md).

Výchozí program knihovny MFC zahrnuje C++ (CPP) zdrojové soubory, soubory prostředků (.rc) a soubor projektu (.vcxproj). Kód generovaný v těchto souborech starter je založena na knihovně MFC.

Následující ukázka seznamu jsou uvedeny úkoly a typy rozšíření pro ovládací prvek ActiveX:

- [Optimalizace ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-optimization.md)

- [Přidání uložených událostí do ovládacího prvku ActiveX](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [Přidání vlastních událostí](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [Přidání uložených metod](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [Přidání vlastních metod](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [Přidání uložených vlastností](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [Přidání vlastních vlastností](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>Přehled

Tato stránka průvodce popisuje aktuální nastavení aplikace pro projekt ovládacího prvku ActiveX knihovny MFC, kterou vytváříte. Ve výchozím nastavení Průvodce vytvoří projekt následujícím způsobem:

- Výchozí projekt negeneruje žádné soubory licence nebo nápovědy za běhu. Tato výchozí nastavení můžete změnit na [nastavení aplikace](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) stránky. Pouze výběr provedené na této stránce Průvodce ovládacím prvkem ActiveX, se projeví ve **přehled** stránky.

- Projekt obsahuje ovládací prvek třídy a třídy stránky vlastností na základě názvu projektu. Můžete upravit název vašeho projektu a souboru názvy na [názvy ovládacích prvků](../../mfc/reference/control-names-mfc-activex-control-wizard.md) stránky.

- Ovládací prvek je založen na žádný existující ovládací prvek Windows, aktivuje se, když se zobrazí, má uživatelské rozhraní a zahrnuje **o** dialogové okno. Tato výchozí nastavení můžete změnit na [nastavení](../../mfc/reference/control-settings-mfc-activex-control-wizard.md) stránky.

## <a name="see-also"></a>Viz také:

[Vytváření a spravování projektů Visual C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[Typy projektů Visual C++](../../build/reference/visual-cpp-project-types.md)<br/>
[Koncepty](../../atl/active-template-library-atl-concepts.md)
