---
title: "Kontejnery ovládacích prvků ActiveX: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5a608d98b43e6daf340ab09c7adb275849f347a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>ActiveX – kontejnery ovládacích prvků: Programování ovládacích prvků ActiveX v kontejneru ovládacího prvku ActiveX
Tento článek popisuje proces pro přístup k zveřejněné [metody](../mfc/mfc-activex-controls-methods.md) a [vlastnosti](../mfc/mfc-activex-controls-properties.md) embedded ovládacích prvků ActiveX. V podstatě postupujte podle těchto kroků:  
  
1.  [Vložení ovládacího prvku ActiveX do projektu kontejneru ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) pomocí galerie.  
  
2.  [Definování proměnné člena](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (nebo jinou formu přístup) stejného typu jako ActiveX třídu obálky ovládacího prvku.  
  
3.  [Program ovládacího prvku ActiveX](#_core_programming_the_activex_control) pomocí předdefinovaných členské funkce obálkové třídy.  
  
 V tomto výkladu předpokládají, že jste vytvořili na základě dialogové okno projektu (s názvem kontejneru) s podporou ovládací prvek ActiveX. Str Ukázka ovládacího prvku, str, přidá do výsledného projektu.  
  
 Jakmile ovládacího prvku str vložený do projektu (krok 1), vložte do dialogové okno aplikace hlavní instanci ovládacího prvku str.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Přidání ovládacího prvku str do šablony dialogového okna  
  
1.  Načtení projektu kontejneru ovládacího prvku ActiveX. V tomto příkladu použijte `Container` projektu.  
  
2.  Klikněte na kartu zobrazení prostředků.  
  
3.  Otevřete **dialogové okno** složky.  
  
4.  Dvakrát klikněte na šablonu pole hlavním dialogu. V tomto příkladu použijte **IDD_CONTAINER_DIALOG**.  
  
5.  Klikněte na ikonu str ovládacího prvku na panelu nástrojů.  
  
6.  Klikněte na pozici v rámci dialogového vložení ovládacího prvku str.  
  
7.  Z **soubor** nabídce zvolte **Uložit vše** se uložit všechny změny šablony pole dialogového okna.  
  
## <a name="modifications-to-the-project"></a>Změny v projektu  
 Pokud chcete povolit aplikaci kontejneru str řízení přístupu, Visual C++ automaticky přidá obálkovou třídu (`CCirc`) soubor implementace (. CPP) do projektu kontejneru a hlavičku obálku – třída (. H) souboru k souboru dialogové okno pole hlavičky:  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a>Záhlaví obálku – třída (. H) soubor  
 Získání a nastavení vlastností (a volat metody) pro řízení str, `CCirc` Obálková třída poskytuje deklaraci všechny zveřejněné metod a vlastností. V příkladu se tyto deklarace nacházejí v MSC H. Následující příklad je část třídy `CCirc` zveřejněné rozhraní ovládacího prvku ActiveX, který definuje:  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 Tato funkce může být volána z jiných postupů aplikace pomocí normální syntaxe jazyka C++. Další informace o použití této funkce člen umožnit přístup k vlastnosti a metody ovládacího prvku, najdete v části [programování ovládacího prvku ActiveX](#_core_programming_the_activex_control).  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a>Členské proměnné změny v projektu  
 Jakmile ovládacího prvku ActiveX je přidán do projektu a vložených v dialogovém okně pole kontejneru, byla přístupná pomocí dalších částí projektu. Nejjednodušší způsob, jak řízení přístupu je [vytvořit členské proměnné](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) dialogu třídy `CContainerDlg` (krok 2), který je stejného typu jako obálkovou třídu přidaných do projektu Visual C++. Členské proměnné pak můžete kdykoli získat přístup k vloženému ovládacímu prvku.  
  
 Když **přidání členské proměnné** přidá dialogové okno `m_circctl` člen proměnné do projektu, přidá také následující řádky do soubor hlaviček (. H) z `CContainerDlg` třídy:  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 Kromě toho volání **ddx_control –** je automaticky přidán do `CContainerDlg`na provádění `DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a>Programování ovládacího prvku ActiveX  
 V tomto okamžiku jste vložili ovládací prvek ActiveX do vaší šablony dialogového okna a vytvořili členské proměnné. Nyní můžete běžné syntaxe C++ pro přístup k vlastnosti a metody vloženému ovládacímu prvku.  
  
 Jak jsme uvedli (v [záhlaví obálku – třída (. H) souboru](#_core_the_wrapper_class_header_28h29_file)), soubor hlaviček (. H) pro `CCirc` obálkovou třídu v této případu msc H, obsahuje seznam členských funkcí, které můžete použít k získání a nastavení hodnotou zveřejněné vlastnost. Členské funkce pro zveřejněné metody jsou k dispozici.  
  
 Je běžné Úprava vlastností ovládacího prvku se v `OnInitDialog` členské funkce hlavním dialogu třídy. Tato funkce je volána těsně před se zobrazí dialogové okno a slouží k inicializaci její obsah, včetně jeho ovládací prvky.  
  
 Následující příklad kódu používá `m_circctl` členské proměnné můžete změnit vlastnosti titulku a CircleShape embedded str ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [ActiveX – kontejnery ovládacích prvků](../mfc/activex-control-containers.md)

