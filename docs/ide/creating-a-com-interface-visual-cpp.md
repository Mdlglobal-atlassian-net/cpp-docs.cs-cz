---
title: Vytváření rozhraní modelu COM (Visual C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.creating.interfaces
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e573e65e1b9f3638aaa2f1b25c36d6c959f194d8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390088"
---
# <a name="creating-a-com-interface-visual-c"></a>Vytváření rozhraní modelu COM (Visual C++)

Průvodci a šablony, pokud chcete vytvářet projekty, které používají rozhraní COM a odesílající rozhraní pro objekty COM a automatizační třídy poskytuje jazyk Visual C++.

Tito průvodci můžete provádět následující tři běžné úlohy:

- [Přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)

   Přidat podporu ATL do MFC aplikace po vytvoření projektu knihovny MFC pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md) a následné spuštění **přidání podpory knihovny ATL do MFC** Průvodce kódem. Tato podpora se vztahuje pouze na jednoduché objekty modelu COM, přidat do spustitelného souboru knihovny MFC ani do projektu knihovny DLL. Tyto objekty knihovny ATL může mít více rozhraní.

- [Vytvoření ovládacího prvku ActiveX prostředí MFC](../mfc/reference/creating-an-mfc-activex-control.md)

   Otevřít [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md) vytvoření ovládacího prvku ActiveX dispinterface a mapu událostí definovaných v souboru IDL a třídu ovládacího prvku, v uvedeném pořadí.

- [Přidání ovládacího prvku ATL](../atl/reference/adding-an-atl-control.md)

   Pomocí kombinace [Průvodce projektem ATL](../atl/reference/atl-project-wizard.md) a [Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md) vytvořit ovládací prvek ActiveX knihovny ATL.

   Můžete také přidat ovládacího prvku ATL do projektu knihovny MFC, do které jste přidali podporu ATL, jak je popsáno výše. Kromě toho pokud vyberete **ovládací prvek ATL** v **přidat třídu** dialogové okno kde ještě nepřidali podporu ATL do projektu knihovny MFC, Visual Studio zobrazí dialogové okno pro potvrzení přidání podpory knihovny ATL do vaší Projekt knihovny MFC.

   Tento průvodce vygeneruje zdroj IDL a mapy modelu COM ve třídách projektu.

Jakmile máte projekt knihovny ATL, otevřít, [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno umožňuje volbu Další průvodci a šablony pro přidání rozhraní modelu COM do vašeho projektu. Následující průvodci vám umožňují vytvořit jeden nebo více rozhraní pro objekt:

- [Průvodce komponentami ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)

- [Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md)

- [Průvodce komponentami ATL Active Server Pages](../atl/reference/atl-active-server-page-component-wizard.md)

- [Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)

Kromě toho můžete implementovat nové rozhraní ovládacího prvku COM tak, že kliknete pravým tlačítkem objekt třídy ovládacího prvku v zobrazení tříd a kliknete [implementovat rozhraní](../ide/implement-interface-wizard.md).

> [!NOTE]
>  Visual Studio neposkytuje průvodce můžete přidat rozhraní do projektu. Můžete přidat rozhraní do projektu knihovny ATL nebo do [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) tak Přidání jednoduchého objektu pomocí [Průvodce jednoduchý objekt knihovny ATL](../atl/reference/atl-simple-object-wizard.md). Můžete také otevřít soubor .idl projektu a vytvořte rozhraní tak, že zadáte:

```
interface IMyInterface {
};

```

Zobrazit [implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Další informace.

Visual C++ poskytuje několik způsobů, jak zobrazit a [úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md) definované pro vaše projekty. [Zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code) zobrazuje ikony pro jakékoli rozhraní nebo dispinterface definované v souboru IDL v projektu jazyka C++.

Zobrazení tříd pro objekt třídy založený na knihovně ATL COM, přečte mapy modelu COM v ATL – třídy zobrazíte vztah mezi ATL – třídy a rozhraní, které implementuje.

V zobrazení tříd a jeho místní nabídky můžete pracovat s rozhraním následujícím způsobem:

- Přidáte objekty knihovny ATL do aplikace založené na knihovně MFC.

- Přidejte metody, vlastnosti a události.

- Dvojitým kliknutím na položku přejít přímo do kódu rozhraní položky.

## <a name="see-also"></a>Viz také

[Tvorba desktopových projektů pomocí průvodců aplikací](../ide/creating-desktop-projects-by-using-application-wizards.md)<br>
[Přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md)