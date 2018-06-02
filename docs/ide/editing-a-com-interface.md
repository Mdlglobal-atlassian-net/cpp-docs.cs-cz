---
title: Úpravy rozhraní modelu COM | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.editing.interfaces
dev_langs:
- C++
helpviewer_keywords:
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 6c2909e0-af2d-4a37-bb39-ed372e6129cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd7a61593a1024c00c0fd0de6bd62ff3ee9323b3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33338679"
---
# <a name="editing-a-com-interface"></a>Úpravy rozhraní modelu COM
Pomocí příkazů z místní nabídky Zobrazení tříd můžete definovat nové metody a vlastnosti pro rozhraní modelu COM v projektech Visual C++. Kromě toho z panelu nástrojů můžete definovat události pro ovládací prvky ActiveX.  
  
 Pro knihovny ATL a MFC – třídy založené na modelu COM objekt můžete upravit implementaci třídy ve stejnou dobu úpravou rozhraní.  
  
> [!NOTE]
>  Pro rozhraní, které jste definovali mimo **přidat třídu** dialogové okno, Visual C++ přidá metody nebo vlastnosti do souboru IDL a přidá do třídy, které implementují metody, i když jsou rozhraní přidat ručně.  
  
 Následující tři průvodce můžete přizpůsobit existující rozhraní. Jsou k dispozici v zobrazení tříd:  
  
|Průvodce|Typ projektu|  
|------------|------------------|  
|[Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md)|Projekty knihovny ATL nebo MFC podpora ATL. Klikněte pravým tlačítkem na rozhraní, do které chcete přidat vlastnost.<br /><br /> Visual C++ zjistí typ projektu a upraví možnosti v průvodci Přidat vlastnost odpovídajícím způsobem:<br /><br /> -Pro odesílající rozhraní v projektech vytvořených pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), zobrazí Průvodce přidáním vlastnosti poskytuje možnosti konkrétní s knihovnou MFC.<br />-Pro rozhraní MFC ActiveX ovládacího prvku Průvodce přidáním vlastnosti poskytuje seznam uložených metod a vlastností, které lze použít v souladu s nebo upravit pro vaše ovládací prvek.<br />-Pro ostatní rozhraní Průvodci přidat vlastnost poskytují možnosti, které jsou užitečné ve většině případů.|  
|[Průvodce přidáním metody](../ide/add-method-wizard.md)|Projekty knihovny ATL nebo MFC podpora ATL. Klikněte pravým tlačítkem na rozhraní, do které chcete přidat metodu.<br /><br /> Visual C++ zjistí typ projektu a upraví možnosti v Průvodce přidáním metody odpovídajícím způsobem:<br /><br /> -Pro odesílající rozhraní v projektech vytvořených pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), Průvodce přidáním metody vyvolání poskytuje možnosti konkrétní s knihovnou MFC.<br />-Pro rozhraní MFC ActiveX ovládacího prvku Průvodce přidáním metody poskytuje seznam uložených metod a vlastností, které lze použít v souladu s nebo upravit pro vaše ovládací prvek.<br />-Pro ostatní rozhraní **přidat metodu** nabídnou možnosti užitečné ve většině případů.|  
  
 Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM pravým tlačítkem myši na ovládací prvek třídy objektu v zobrazení tříd a kliknutím na [implementovat rozhraní](../ide/implement-interface-wizard.md).  
  
## <a name="see-also"></a>Viz také  
 [Práce se zdrojovými soubory](../windows/working-with-resource-files.md)   
 [Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Typy projektů Visual C++](../ide/visual-cpp-project-types.md)