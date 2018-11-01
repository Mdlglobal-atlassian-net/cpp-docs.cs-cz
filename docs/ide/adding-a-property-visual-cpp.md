---
title: Přidání vlastnosti (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
ms.openlocfilehash: 3c47a5b50442f47e6042ea1232590dbdde7299ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50563082"
---
# <a name="adding-a-property-visual-c"></a>Přidání vlastnosti (Visual C++)

Můžete použít [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md) přidání metody do rozhraní ve vašem projektu.

### <a name="to-add-a-property-to-your-object"></a>Přidání vlastnosti do objektu

1. V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na název rozhraní, ke kterému chcete přidat vlastnost.

   > [!NOTE]
   > Můžete také přidat vlastnosti do odesílacích rozhraních, která pokud je projekt s atributy, jsou vnořené uvnitř uzlu knihovny.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat vlastnost**.

1. V [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md), zadejte informace k vytvoření vlastnosti.

1. Zadejte nastavení jakékoli interface definition language (IDL) pro vlastnost [IDL – atributy](../ide/idl-attributes-add-property-wizard.md) stránky průvodce.

1. Klikněte na tlačítko **Dokončit** přidat vlastnost.

**Získat** a `Put` metody, vlastnosti se zobrazí jako dvě ikony v zobrazení tříd v rámci rozhraní, kde je definován. Dvakrát klikněte na ikonu se zobrazí deklarace vlastnosti v souboru IDL.

- Pro rozhraní knihovny ATL **získat** a **umístit** funkce jsou přidány do souboru CPP, a odkazy na tyto funkce jsou přidány do souboru hlaviček.

- Pro odesílající rozhraní knihovny MFC, pokud vyberete **členskou proměnnou** jako typ implementace metody a proměnné se přidají do třídy, která jej implementuje. Pokud vyberete **metody Get/Set** jako typ implementace jsou přidány dvě metody do třídy, která jej implementuje.

## <a name="see-also"></a>Viz také

[Vytváření rozhraní modelu COM](../ide/creating-a-com-interface-visual-cpp.md)<br>
[Úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md)<br>
[Component Object Model](/windows/desktop/com/the-component-object-model)<br>
[Ukazatele rozhraní a rozhraní](/windows/desktop/com/interface-pointers-and-interfaces)