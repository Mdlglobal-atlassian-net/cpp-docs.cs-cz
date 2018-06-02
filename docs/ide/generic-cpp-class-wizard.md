---
title: Průvodce obecnými třídami C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 43e86a4047ef025f49dd01eda90f324623a90752
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "33328302"
---
# <a name="generic-c-class-wizard"></a>Průvodce obecnými třídami C++
Přidá obecnými třídami C++ do projektu. Třída nedědí z knihovny ATL nebo MFC.  
  
 **Název třídy**  
 Nastaví název nové třídy.  
  
 **soubor h**  
 Nastaví název hlavičky souboru pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **název třídy**. Uložte soubor hlaviček umístění podle vaší volby, nebo deklaraci třídy připojit k existující soubor, klikněte na tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k určení, zda by měl deklaraci třídy přiložit do obsahu souboru. Chcete-li připojit deklaraci, klikněte na tlačítko **Ano**; Chcete-li se vraťte do průvodce a zadejte jiný název souboru, klikněte na tlačítko **ne**.  
  
 **souboru**  
 Nastaví název souboru implementace pro novou třídu. Ve výchozím nastavení, tento název je založen na názvu poskytují v **název třídy**. Uložte soubor implementace umístění podle vaší volby, nebo připojit k existující soubor definice třídy, klikněte na tlačítko se třemi tečkami (**...** ). Pokud zadáte existující soubor, po kliknutí na tlačítko **Dokončit**, Průvodce zobrazí výzvu k určení, zda by měl definici třídy přiložit k obsahu souboru. Připojit definici, klikněte na tlačítko **Ano**; Chcete-li se vraťte do průvodce a zadejte jiný název souboru, klikněte na tlačítko **ne**.  
  
 **Base – třída**  
 Nastaví základní třídu pro novou třídu.  
  
 **Přístup**  
 Nastaví přístup na členy základní třídy pro novou třídu. Modifikátory přístupu jsou klíčová slova, které určují úroveň přístupu, které ostatní třídy členské funkce tříd. Další informace o tom, jak zadat přístupu najdete v tématu [řízení přístupu ke členu](../cpp/member-access-control-cpp.md). Ve výchozím nastavení je úroveň přístupu třída nastavena na `public`.  
  
-   `public`  
  
-   `protected`  
  
-   `private`  
  
-   **Výchozí** (žádné – modifikátor přístupu se vygeneruje.)  
  
 **Virtuální – destruktor**  
 Určuje, jestli je virtuální destruktoru třídy. Použití virtuální destruktor pomáhá zajistit, že správné – destruktor je volána, když se odstraní instanci odvozené třídy.  
  
 **Vložené**  
 Generuje konstruktoru třídy a definice třídy jako vložené funkce v záhlaví souboru.  
  
 **Spravované**  
 Při výběru, přidá soubor spravované třídy a hlavičky. Není-li zaškrtnuto, přidá soubor nativní třídy a hlavičky.  
  
## <a name="see-also"></a>Viz také  
 [Přidání generické třídy jazyka C++](../ide/adding-a-generic-cpp-class.md)