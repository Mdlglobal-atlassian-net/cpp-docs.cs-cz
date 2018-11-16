---
title: Přidání generické třídy jazyka C++
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: 08ebe572da605e0f6d4d712bd7e48159598ba844
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694137"
---
# <a name="add-a-generic-c-class"></a>Přidání generické třídy jazyka C++

Můžete přidat obecnou C++ třídu pomocí **zobrazení tříd**. Generické třídy jazyka C++ je třída, která definujete nebo, která je odvozena z třídy, které definujete.

**Přidání generické třídy jazyka C++ do projektu:**

1. V **zobrazení tříd**, klikněte pravým tlačítkem na projekt, ke kterému chcete přidat novou třídu, zvolte **přidat**a klikněte na tlačítko **třídy**.

1. V [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno, v podokně šablony vyberte **třídy C++**. Vyberte **přidat** zobrazíte [Průvodci obecnými třídami C++](#generic-c-class-wizard).

1. V průvodci zadejte název třídy a potom definovat nastavení nebo přijměte výchozí hodnoty.

1. Chcete-li ukončit průvodce a zobrazit nové generické třídy jazyka C++ v projektu, vyberte **Dokončit**.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodci obecnými třídami C++](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Průvodci obecnými třídami C++

Do projektu přidá generické třídy jazyka C++. Třída nedědí z knihovny ATL nebo MFC.

- **Název třídy**

  Nastaví název nové třídy.

- **soubor .h**

  Nastaví název souboru hlaviček pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Uložte soubor hlaviček do umístění podle vašeho výběru, nebo deklaraci třídy připojit k existujícímu souboru, vyberte tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor a vyberte **Dokončit**, Průvodce zobrazí výzvu k určení, zda deklarace třídy by měl být připojen do obsahu souboru. Chcete-li přidat deklaraci, vyberte **Ano**; pokud ho chcete vrátit do průvodce a zadejte jiný název souboru, vyberte **ne**.

- **soubor .cpp**

  Nastaví název implementačního souboru pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Uložit implementační soubor do umístění podle vašeho výběru, nebo připojit k existujícímu souboru definice třídy, vyberte tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor a vyberte **Dokončit**, Průvodce zobrazí výzvu k určení, zda má být definici třídy připojen do obsahu souboru. Chcete-li přidat definici, vyberte **Ano**; pokud ho chcete vrátit do průvodce a zadejte jiný název souboru, vyberte **ne**.

- **Základní třída**

  Nastaví základní třídu pro novou třídu.

- **Přístup**

  Nastaví přístup ke členům základní třídy pro novou třídu. Modifikátory přístupu jsou klíčová slova, které určují úroveň přístupu, které mají jiné třídy pro členské funkce třídy. Další informace o tom, jak určit přístup, najdete v části [řízení přístupu ke členu](../cpp/member-access-control-cpp.md). Ve výchozím nastavení je úroveň přístupu třídy nastavena na `public`.

  - `public`
  - `protected`
  - `private`
  - **Výchozí** (je generována žádná modifikátor přístupu.)

- **Virtuální destruktor**

  Určuje, zda je virtuální destruktor třídy. Použijte virtuální destruktor pomáhá se ujistit, že správný destruktor se volá, když se odstraní výskyty odvozené třídy.

- **vložené**

  Generuje konstruktoru třídy a definice třídy jako vložené funkce v hlavičkovém souboru.

- **Spravované**

  Když vyberete, přidá spravované třídy a záhlaví souboru. Není-li zaškrtnuto, přidá nativní soubor třídy a záhlaví.
