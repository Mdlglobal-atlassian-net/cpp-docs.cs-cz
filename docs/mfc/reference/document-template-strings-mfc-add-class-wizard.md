---
title: Řetězce šablon dokumentů, Průvodce přidáním třídy MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: 167ddb7fd6beabe734eb58e8b17355166b86445d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385415"
---
# <a name="document-template-strings-mfc-add-class-wizard"></a>Řetězce šablony dokumentu, Průvodce přidáním třídy MFC

Tato stránka průvodce je k dispozici pouze pro třídy, které splňují následující kritéria:

- V projektu knihovny MFC podporuje architekturu document/view.

- Je základní třídy novou třídu [CFormView](../../mfc/reference/cformview-class.md).

- Zaškrtněte políčko **generovat DocTemplate prostředky** proběhne na **názvy** část [Průvodce třídami MFC](../../mfc/reference/mfc-add-class-wizard.md).

Průvodce poskytuje výchozí hodnoty pro následující hodnoty usnadňující návrh zobrazení formulářů, správu a lokalizaci. Protože většina řetězce šablony dokumentu jsou viditelné a používá ji uživatelé formuláře, jsou lokalizovány do **jazyk prostředku** podle [typy aplikací](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací MFC Vytvoření projektu.

> [!NOTE]
>  Průvodce neposkytuje Automatická podpora funkce tisku pro třídy odvozené z `CFormView`.

Zobrazit [šablony dokumentů a proces vytváření dokumentů/zobrazení](../../mfc/document-templates-and-the-document-view-creation-process.md) Další informace.

## <a name="nonlocalized-strings"></a>Řetězce nelokalizované

Platí pro aplikace, které vytvářejí dokumenty uživatele. Uživatelé mohou otevřít a uložit dokumenty snadněji, pokud typ dokument má příponu souboru a ID typu souboru. Tyto položky nejsou lokalizovány, protože jsou použity v systému, nikoli podle uživatele.

- **Přípona souboru**

   Nastaví přípona souboru, který je přidružený k typu dokumentu pro tuto aplikaci formulářů. Výchozí přípona souboru na základě názvu třídy. Například, pokud je název nové třídy knihovny MFC `CWidget`, ve výchozím nastavení, je přípona. WID Přípona souboru je použít ve filtrech souborů a **otevřít** a **uložit jako** dialogových oknech.

   Pokud změníte příponu souboru, změna se projeví v **název filtru** pole.

   > [!NOTE]
   > Pokud změníte výchozí příponu, nezahrnujte období.

- **ID typu souboru**

   Nastaví název typu dokumentu v systémovém registru.

## <a name="localized-strings"></a>Lokalizované řetězce

Vytváří řetězce, které jsou spojené s formuláři a dokumenty, které čtou a používat uživatelů aplikace.

- **Název typu dokumentu**

   Určuje typ dokumentu, pod kterým mohou být seskupeny dokumentu aplikace. Ve výchozím nastavení je založen na názvu třídy. Například, pokud je název nové třídy knihovny MFC **CWidget**, ve výchozím nastavení je název typu dokumentu widgetu. Změna výchozího další možnosti v tomto dialogovém nezmění.

- **Název filtru**

   Nastaví název, který mohou uživatelé označit k vyhledání souborů typu zadaného souboru. Tato možnost je k dispozici **soubory typu** a **uložit jako typ** možnosti v standardní Windows **otevřít** a **uložit jako** dialogových oknech. Ve výchozím nastavení, je název založené na název projektu a soubory, za nímž následuje rozšíření podle **přípona souboru**. Pokud váš projekt má název widgetu a přípona souboru je WID, například **název filtru** ve výchozím nastavení je Widget soubory (*.wid).

- **Nový krátký název souboru**

   Nastaví název zobrazovaný v standardní Windows **nový** dialogové okno, pokud projekt obsahuje více než jedna šablona dokumentu. Pokud je vaše aplikace [automatizační server](../../mfc/automation-servers.md), tento název se používá jako krátký název objektu automatizace. Ve výchozím nastavení tento název je založen na názvu třídy.

- **Dlouhý název typu souboru**

   Nastaví název typu souboru v systémovém registru. Pokud vaše aplikace je automatizační server, tento název se používá jako dlouhý název objektu automatizace. Ve výchozím nastavení tento název je založen na názvu třídy plus. Dokument. Například, pokud je název třídy `CWidget`, **typ souboru dlouhého názvu** je Widget dokumentu.

- **Třída dokumentu**

   Určuje třídy dokumentu v projektu. Ve výchozím nastavení, tato třída je hlavní aplikace dokumentové třídy, jak je uvedeno v [třídy generované v revizi](../../mfc/reference/generated-classes-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC. V seznamu můžete vybrat jiné třídy dokumentu, pokud jste přidali další třídy dokumentu v projektu.

## <a name="see-also"></a>Viz také

[Průvodce přidáním třídy MFC](../../mfc/reference/mfc-add-class-wizard.md)<br/>
[Třída knihovny MFC](../../mfc/reference/adding-an-mfc-class.md)<br/>
[Přidání třídy](../../ide/adding-a-class-visual-cpp.md)
