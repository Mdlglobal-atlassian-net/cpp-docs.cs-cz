---
title: "Průvodce obecnými třídami C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.generic
dev_langs:
- C++
helpviewer_keywords:
- Generic C++ Class Wizard [C++]
ms.assetid: aa95be9e-fc1b-45db-a11d-0d32c4929077
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 82d706c30c729f490f6bfdec3344d5dab537a689
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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