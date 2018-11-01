---
title: Průvodce obecnými třídami C++
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.class.generic
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
ms.openlocfilehash: e3db091585615dcdccaab7c99c18a923802b31a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451035"
---
# <a name="generic-c-class-wizard"></a>Průvodce obecnými třídami C++

Do projektu přidá generické třídy jazyka C++. Třída nedědí z knihovny ATL nebo MFC.

- **Název třídy**

   Nastaví název nové třídy.

- **soubor .h**

   Nastaví název souboru hlaviček pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Uložte soubor hlaviček do umístění podle vašeho výběru, nebo deklaraci třídy připojit k existujícímu souboru, klikněte na tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor, po kliknutí na **Dokončit**, Průvodce zobrazí výzvu k určení, zda by měla být k obsah souboru připojen deklaraci třídy. Přidat deklaraci, klikněte na tlačítko **Ano**; pokud ho chcete vrátit do průvodce a zadejte jiný název souboru, klikněte na tlačítko **ne**.

- **soubor .cpp**

   Nastaví název implementačního souboru pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu je zadat v **název třídy**. Uložte soubor implementace do umístění podle vaší volby, nebo připojit k existujícímu souboru definice třídy, klikněte na tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor, po kliknutí na **Dokončit**, Průvodce zobrazí výzvu k určení, zda má být definici třídy připojen do obsahu souboru. Přidat definici, klikněte na tlačítko **Ano**; pokud ho chcete vrátit do průvodce a zadejte jiný název souboru, klikněte na tlačítko **ne**.

- **Základní třída**

   Nastaví základní třídu pro novou třídu.

- **Přístup**

   Nastaví přístup ke členům základní třídy pro novou třídu. Modifikátory přístupu jsou klíčová slova, které určují úroveň přístupu, které mají jiné třídy pro členské funkce třídy. Další informace o tom, jak určit přístup, najdete v části [řízení přístupu ke členu](../cpp/member-access-control-cpp.md). Ve výchozím nastavení je úroveň přístupu třídy nastavena na `public`.

   - `public`

   - `protected`

   - `private`

   - **Výchozí** (je generována žádná modifikátor přístupu.)

- **Virtuální destruktor**

   Určuje, zda je virtuální destruktor třídy. Použijte virtuální destruktor pomáhá zajistit, že správný destruktor se volá, když se odstraní výskyty odvozené třídy.

- **vložené**

   Generuje konstruktoru třídy a definice třídy jako vložené funkce v hlavičkovém souboru.

- **Spravované**

   Když vyberete, přidá spravované třídy a záhlaví souboru. Není-li zaškrtnuto, přidá nativní soubor třídy a záhlaví.

## <a name="see-also"></a>Viz také

[Přidání generické třídy jazyka C++](../ide/adding-a-generic-cpp-class.md)