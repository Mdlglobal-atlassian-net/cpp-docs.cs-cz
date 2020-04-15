---
title: 'ActiveX – kontejnery ovládacích prvků: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
ms.openlocfilehash: 9620f4d47197147db4972c9f2024f6018a705902
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371191"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX – kontejnery ovládacích prvků: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX

Tento článek popisuje proces přístupu k exponovaným [metodám](../mfc/mfc-activex-controls-methods.md) a [vlastnostem](../mfc/mfc-activex-controls-properties.md) vložených ovládacích prvků ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

V podstatě budete postupovat podle následujících kroků:

1. [Vložte ovládací prvek ActiveX do projektu kontejneru ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) pomocí galerie.

1. [Definujte členovou proměnnou](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (nebo jinou formu přístupu) stejného typu jako třídu obálky ovládacího prvku ActiveX.

1. [Naprogramujte ovládací prvek ActiveX](#_core_programming_the_activex_control) pomocí předdefinovaných členských funkcí obálky.

V této diskusi předpokládejme, že jste vytvořili projekt založený na dialogu (s názvem Kontejner) s podporou ovládacího prvku ActiveX. Řízení vzorku Circ, Circ, budou přidány do výsledného projektu.

Po vložení ovládacího prvku Circ do projektu (krok 1) vložte instanci ovládacího prvku Circ do hlavního dialogového okna aplikace.

## <a name="procedures"></a>Procedury

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Přidání ovládacího prvku Circ do šablony dialogového okna

1. Načtěte projekt kontejneru ovládacího prvku ActiveX. V tomto příkladu `Container` použijte projekt.

1. Klikněte na kartu Zobrazení zdrojů.

1. Otevřete složku **Dialog.**

1. Poklepejte na šablonu hlavního dialogového okna. V tomto příkladu použijte **IDD_CONTAINER_DIALOG**.

1. Klepněte na ikonu ovládacího prvku Circ v panelu nástrojů.

1. Klepnutím na místo v dialogovém okně vložte ovládací prvek Circ.

1. V nabídce **Soubor** zvolte **Uložit vše,** chcete-li uložit všechny změny do šablony dialogového okna.

## <a name="modifications-to-the-project"></a>Změny projektu

Chcete-li povolit aplikaci Container přístup k ovládacímu prvku Circ, Visual C++ automaticky přidá soubor implementace obálky (`CCirc`) (. CPP) do projektu Container a hlavičky obálkové třídy (. H) do souboru záhlaví dialogového okna:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

## <a name="the-wrapper-class-header-h-file"></a><a name="_core_the_wrapper_class_header_28h29_file"></a>Záhlaví třídy obálky (. H) Soubor

Chcete-li získat a nastavit vlastnosti (a vyvolat `CCirc` metody) pro circ ovládacího prvku, obálka třída poskytuje deklaraci všech exponovaných metod a vlastností. V příkladu se tyto deklarace nacházejí v CIRC. H. Následující ukázka je část `CCirc` třídy, která definuje exponovaná rozhraní ovládacího prvku ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Tyto funkce pak lze volat z jiných postupů aplikace pomocí normální syntaxe jazyka C++. Další informace o použití této sady členských funkcí pro přístup k metodám a vlastnostem ovládacího prvku naleznete v části [Programování ovládacího prvku ActiveX](#_core_programming_the_activex_control).

## <a name="member-variable-modifications-to-the-project"></a><a name="_core_member_variable_modifications_to_the_project"></a>Členské proměnné změny projektu

Jakmile je ovládací prvek ActiveX přidán do projektu a vložen do kontejneru dialogového okna, je přístupný jinými částmi projektu. Nejjednodušší způsob, jak získat přístup k ovládacímu prvku, `CContainerDlg` je [vytvořit členovou proměnnou](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) třídy dialog (krok 2), která je stejného typu jako třída obálky přidaná do projektu visual c++. Potom můžete použít proměnnou člena pro přístup k vložený ovládací prvek kdykoli.

Když dialogové okno **Přidat proměnnou člena** přidá do projektu proměnnou *m_circctl* člen, přidá také následující řádky do souboru záhlaví (. H) třídy: `CContainerDlg`

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Kromě toho je výzva **k DDX_Control** `CContainerDlg`automaticky přidána `DoDataExchange`k provádění aplikace :

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

## <a name="programming-the-activex-control"></a><a name="_core_programming_the_activex_control"></a>Programování ovládacího prvku ActiveX

V tomto okamžiku jste vložili ovládací prvek ActiveX do šablony dialogového okna a vytvořili pro něj členní proměnnou. Nyní můžete použít společnou syntaxi jazyka C++ pro přístup k vlastnostem a metodám vloženého ovládacího prvku.

Jak je uvedeno (v [záhlaví třídy obálky (. H) Soubor](#_core_the_wrapper_class_header_28h29_file)), soubor záhlaví (. H) pro `CCirc` obálkovou třídu, v tomto případě CIRC. H, obsahuje seznam členských funkcí, které můžete použít k získání a nastavení jakékoli hodnoty exponované vlastnosti. K dispozici jsou také členské funkce pro exponované metody.

Společné místo pro úpravu vlastností ovládacího prvku je v `OnInitDialog` členské funkci hlavní třídy dialogu. Tato funkce je volána těsně před zobrazením dialogového okna a slouží k inicializaci jeho obsahu, včetně všech jeho ovládacích prvků.

Následující příklad kódu používá proměnnou *m_circctl* člen k úpravě vlastností Caption a CircleShape vloženého ovládacího prvku Circ:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Viz také

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
