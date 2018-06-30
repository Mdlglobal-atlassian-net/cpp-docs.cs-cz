---
title: Řetězce šablony dokumentu, Průvodce aplikací knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.exe.doctemp
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard, document template strings
ms.assetid: 8109f662-3182-4682-977a-2503321c678a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32d684d7b9b5f8057893d79b864be7b6d9b512fc
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122193"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Řetězce šablon dokumentů, Průvodce aplikací MFC
Na této stránce Průvodce aplikací MFC zadejte nebo upřesněte následující možnosti, které pomáhají při správě dokumentů a lokalizace. Řetězce šablony dokumentu jsou k dispozici pro aplikace, které zahrnují **Document/view – architektura podporu** v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md). Nejsou k dispozici pro dialogová okna. Protože většina řetězce šablony dokumentu je viditelná a použitá s aplikace, jsou lokalizovány do **jazyk prostředku** uvedené v **typ aplikace** stránce průvodce.  
  
 **Nelokalizované řetězce**  
 Platí pro aplikace, které vytvářejí dokumenty uživatele. Uživatelé mohli otevřít, vytisknout a uložit dokumenty snadněji, pokud zadáte příponu souboru a ID typu souboru. Tyto položky nejsou lokalizovány, protože se používají v systému, a nikoli uživatele.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Přípona souboru**|Nastaví přípony spojené s dokumenty, které uživatel uloží při používání aplikace. Například pokud projektu jmenuje pomůcky, mohla mít název za příponu zvolit. (Když zadáte příponu souboru, nezahrnujte období.)<br /><br /> Pokud zadáte příponu souboru, můžete Průzkumníku tisk dokumentů aplikace bez spuštění aplikace, když uživatel přesune dokument na ikonu tiskárny.<br /><br /> Pokud nezadáte rozšíření, musí uživatel zadat příponu souboru při ukládání souborů. Průvodce neposkytuje výchozí příponu souboru.|  
|**ID typu souboru**|Nastaví popisek pro typ vašeho dokumentu v registru systému.|  
  
 **Lokalizované řetězce**  
 Vytváří řetězce přidružené aplikace a dokument, který čtou a používá aplikace uživatele.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Jazyk**|Určuje jazyk, ve kterém jsou zobrazeny řetězce pro všechna pole v **lokalizované řetězce**. Chcete-li změnit hodnotu v tomto poli, vyberte požadovaný jazyk v rámci **jazyk prostředku** v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací MFC.|  
|**Titulek hlavního rámce**|Nastaví text, zobrazí v horní části hlavního rámce aplikace. Ve výchozím nastavení je to název projektu.|  
|**Název typu dokumentu**|Určuje typ dokumentu, pod kterým je možné seskupit dokumentu aplikace. Ve výchozím nastavení je to název projektu. Změna výchozí další možnosti v tomto dialogovém nezmění.|  
|**Název filtru**|Nastaví název, který mohou uživatelé použít k vyhledání váš typ souborů. Tato možnost je dostupná z **soubory typu** a **uložit jako typ** možnosti v systému Windows standardní **otevřete** a **uložit jako** dialogová okna. Ve výchozím nastavení název projektu a soubory, a příponu součástí **příponu souboru**. Pokud projektu jmenuje Widget a přípona souboru je, například **název filtru** soubory Widget (*.wgt) je ve výchozím nastavení.|  
|**Nové krátký název souboru**|Nastaví název zobrazovaný v standardní Windows **nový** dialogové okno, pokud existuje více než jednu šablonu dokumentu. Pokud je vaše aplikace [automatizační server](../../mfc/automation-servers.md), tento název se používá jako krátký název objektu automatizace. Ve výchozím nastavení je to název projektu.|  
|**Dlouhý název typu souboru**|Nastaví název typu souboru v registru systému. Pokud je aplikace Automatizační server, tento název se používá jako dlouhý název objektu automatizace. Ve výchozím nastavení je to název projektu a. Dokument.|  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

