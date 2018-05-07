---
title: Řetězce šablony dokumentu, Průvodce přidáním třídy MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.class.mfc.simple.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Add Class Wizard, document control strings
ms.assetid: 14e1c834-5e79-4dbd-811f-ec8f0a9cdcb2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 81b14e0c397ac9179142627bca04b647c1db96db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Řetězce šablony dokumentu, Průvodce přidáním třídy MFC
Tato stránka průvodce je k dispozici pouze pro třídy splňující následující kritéria:  
  
-   V projektu knihovny MFC podporuje architektuře dokument/zobrazení.  
  
-   Základní třída nové třídy je [CFormView](../../mfc/reference/cformview-class.md).  
  
-   Zaškrtněte políčko **Generate DocTemplate resources** se kontroluje na **názvy** části [Průvodce třídou MFC](../../mfc/reference/mfc-add-class-wizard.md).  
  
 Průvodce poskytuje výchozí hodnoty pro následující hodnoty, které pomáhají při návrhu formulářů, správu a lokalizace. Protože většina řetězce šablony dokumentu je viditelná a použitá s formuláře, jsou lokalizovány do **jazyk prostředku** uvedené v [typy aplikací](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací MFC Vytvoření projektu.  
  
> [!NOTE]
>  Průvodce neposkytuje automatickou podporu tisku pro třídy odvozené od `CFormView`.  
  
 V tématu [šablony dokumentů a proces tvorby Document/View –](../../mfc/document-templates-and-the-document-view-creation-process.md) Další informace.  
  
## <a name="nonlocalized-strings"></a>Nelokalizované řetězce  
 Platí pro aplikace, které vytvářejí dokumenty uživatele. Uživatelé mohli otevřít a uložit dokumenty snadněji, pokud má typ dokumentu příponu souboru a ID typu souboru. Tyto položky nejsou lokalizovány, protože se používají v systému, a nikoli uživatele.  
  
 **Přípona souboru**  
 Nastaví přípona souboru, který je přidružený k typu dokumentu pro tuto aplikaci formulářů. Výchozí přípona souboru na základě názvu třídy. Například pokud je název nové třídy MFC **CWidget**, ve výchozím nastavení, přípona souboru je. WID Přípona souboru se používá v filtry souborů a **otevřete** a **uložit jako** dialogová okna.  
  
 Pokud změníte příponu souboru, změna se projeví v **název filtru** pole.  
  
> [!NOTE]
>  Pokud změníte výchozí přípona souboru, nezahrnujte období.  
  
 **ID typu souboru**  
 Nastaví popisek pro typ vašeho dokumentu v registru systému.  
  
## <a name="localized-strings"></a>Lokalizované řetězce  
 Vytváří řetězce přidružené formulářů a dokumenty, které čtou a používá aplikace uživatele.  
  
 **Název typu dokumentu**  
 Určuje typ dokumentu, pod kterým je možné seskupit dokumentu aplikace. Ve výchozím nastavení je založen na název třídy. Například pokud je název nové třídy MFC **CWidget**, ve výchozím nastavení je název typu dokumentu pomůcky. Změna výchozí další možnosti v tomto dialogovém nezmění.  
  
 **Název filtru**  
 Nastaví název, který mohou uživatelé použít pro soubory typu zadaný soubor najít. Tato možnost je dostupná z **soubory typu** a **uložit jako typ** možnosti v systému Windows standardní **otevřete** a **uložit jako** dialogová okna. Ve výchozím nastavení je název založen na název projektu a soubory, a příponu uvedené v **příponu souboru**. Pokud projektu jmenuje Widget a přípona souboru je WID, například **název filtru** soubory Widget (*.wid) je ve výchozím nastavení.  
  
 **Nové krátký název souboru**  
 Nastaví název zobrazovaný v standardní Windows `New` dialogové okno, pokud projekt má více než jedna šablona dokumentu. Pokud je vaše aplikace [automatizační server](../../mfc/automation-servers.md), tento název se používá jako krátký název objektu automatizace. Ve výchozím nastavení je tento název založen na název třídy.  
  
 **Dlouhý název typu souboru**  
 Nastaví název typu souboru v registru systému. Pokud je aplikace Automatizační server, tento název se používá jako dlouhý název objektu automatizace. Ve výchozím nastavení tento název je založen na název třídy plus. Dokument. Například, pokud je název třídy **CWidget**, **typ souboru dlouhý název** je dokument Widget.  
  
 **Třída dokumentu**  
 Určuje třída dokumentu projektu. Ve výchozím nastavení, tato třída je třída dokumentu v hlavní aplikaci, jak je uvedeno v [Přehled vytvořených tříd](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky Průvodce aplikací MFC. V seznamu můžete vybrat jinou třídu dokumentu, pokud jste přidali další třídy dokumentů v projektu.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce přidáním třídy MFC](../../mfc/reference/mfc-add-class-wizard.md)   
 [Třída knihovny MFC](../../mfc/reference/adding-an-mfc-class.md)   
 [Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
