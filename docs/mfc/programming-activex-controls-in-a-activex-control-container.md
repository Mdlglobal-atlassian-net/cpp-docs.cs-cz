---
title: 'Kontejnery ovládacích prvků ActiveX: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX'
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
ms.openlocfilehash: eaeb5275ce825272e1c605e7ceeefa24db7a32ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378112"
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Kontejnery ovládacích prvků ActiveX: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX

Tento článek popisuje proces pro přístup k zveřejněné [metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md) vložený ovládacích prvků ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

V podstatě postupujte podle těchto kroků:

1. [Vložení ovládacího prvku ActiveX v kontejneru projektu ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) pomocí galerie.

1. [Definujte proměnnou člena](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (nebo jiná forma přístup) stejného typu jako ActiveX třídu obálky ovládacího prvku.

1. [Program ovládací prvek ActiveX](#_core_programming_the_activex_control) pomocí předdefinovaných členské funkce obálkovou třídu.

V tomto výkladu Předpokládejme, že jste vytvořili založených na dialogovém okně projekt (kontejneru) s podporou ovládacího prvku ActiveX. Ukázka ovládacího prvku systému KR, KR, se přidají do výsledné projektu.

Jakmile ovládací prvek KR vložíte do projektu (krok 1), vložte do dialogové okno aplikace hlavní instanci ovládacího prvku kr.

## <a name="procedures"></a>Procedury

#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Přidání ovládacího prvku KR k šabloně dialogu

1. Načtení projektu kontejneru ovládacího prvku ActiveX. V tomto příkladu použijte `Container` projektu.

1. Klikněte na kartu zobrazení prostředků.

1. Otevřít **dialogové okno** složky.

1. Dvakrát klikněte šablony hlavní dialogového okna. V tomto příkladu použijte **IDD_CONTAINER_DIALOG**.

1. Klikněte na ikonu KR ovládacího prvku na panelu nástrojů.

1. Klikněte na místě dialogové okno Vložit ovládací prvek str.

1. Z **souboru** nabídce zvolte **Uložit vše** uložte všechny změny šablony dialogového okna.

## <a name="modifications-to-the-project"></a>Změny v projektu

Chcete-li aplikace typu kontejner pro přístup k ovládacím prvku KR, Visual C++ automaticky přidá obálkovou třídu (`CCirc`) implementační soubor (. CPP) do kontejneru projektu a záhlaví třídy obálky (. H) soubor do souboru záhlaví pole dialogové okno:

[!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]

##  <a name="_core_the_wrapper_class_header_28h29_file"></a> Záhlaví třídy obálky (. H) soubor

Získání a nastavení vlastností (a volat metody) ovládacího prvku KR `CCirc` Obálková třída obsahuje deklaraci všechny vystavené metod a vlastností. V tomto příkladu jsou tyto deklarace součástí msc H. Následující příklad je část třídy `CCirc` , který definuje rozhraní vystavené ovládacího prvku ActiveX:

[!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]

Tyto funkce může být volána z jiných postupů vaší aplikace pomocí normální syntaxí jazyka C++. Další informace o používání tato členská funkce, nastavení pro přístup k vlastnosti a metody ovládacího prvku, naleznete v části [programování ovládací prvek ActiveX](#_core_programming_the_activex_control).

##  <a name="_core_member_variable_modifications_to_the_project"></a> Členské proměnné změny v projektu

Jakmile byl přidán do projektu a vložené v kontejneru pole dialogového okna ovládacího prvku ActiveX, byla přístupná z jiných částí projektu. Nejjednodušší způsob, jak řízení přístupu je [vytvořit proměnnou člena](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) dialogové třídy `CContainerDlg` (krok 2), to znamená stejného typu jako Obálková třída, přidaných do projektu Visual C++. Potom můžete členské proměnné pro přístup k vloženému ovládacímu prvku kdykoli.

Při **přidat členskou proměnnou** dialogové okno přidá *m_circctl* členské proměnné do projektu, přidá také následující řádky do souboru hlaviček (. H) z `CContainerDlg` třídy:

[!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]

Kromě toho volání **ddx_control –** se automaticky přidá do `CContainerDlg`vaší implementace `DoDataExchange`:

[!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]

##  <a name="_core_programming_the_activex_control"></a> Programování ovládacího prvku ActiveX

V tomto okamžiku jste vložili ovládacího prvku ActiveX do dialogového okna šablony a vytvořen členské proměnné. Nyní můžete běžné C++ syntaxi pro přístup k vlastnostem a metodám vloženému ovládacímu prvku.

Jak je uvedeno (v [záhlaví třídy obálky (. H) File](#_core_the_wrapper_class_header_28h29_file)), souboru hlaviček (. H) pro `CCirc` obálkové třídy, v tomto případu msc H, obsahuje seznam členské funkce, které můžete použít k získání a nastavení jakoukoli hodnotu vlastnosti zveřejněné. Členské funkce zveřejněné metody jsou také k dispozici.

Probíhá společné místo, kde můžete upravit vlastnosti ovládacího prvku `OnInitDialog` členské funkce třídy hlavním dialogu. Tato funkce je volána těsně před plánovaným dialogové okno se zobrazí a slouží k inicializaci jeho obsah, včetně všech ovládacích prvků.

Následující příklad kódu používá *m_circctl* členské proměnné k úpravě popisek a CircleShape vlastností vloženému ovládacímu prvku KR:

[!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]

## <a name="see-also"></a>Viz také:

[ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)
