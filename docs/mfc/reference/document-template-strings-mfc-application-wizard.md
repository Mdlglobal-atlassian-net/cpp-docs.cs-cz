---
title: Řetězce šablon dokumentů, Průvodce aplikací knihovny MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: a2b1e30ac1e4381cdcd80eddd7fdd4ea27bde5a4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700567"
---
# <a name="document-template-strings-mfc-application-wizard"></a>Řetězce šablon dokumentů, Průvodce aplikací MFC
Na této stránce Průvodce aplikací knihovny MFC poskytují nebo upřesněte následující možnosti, které vám pomůžou s Správa dokumentů a lokalizaci. Řetězce šablony dokumentu jsou k dispozici pro aplikace, které zahrnují **podpora architektury Document/view** v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md). Nejsou k dispozici pro dialogová okna. Protože většina řetězce šablony dokumentu jsou viditelné a používá ji uživatelé vaší aplikace, jsou lokalizovány do **jazyk prostředku** podle **typ aplikace** stránky průvodce.  
  
- **Řetězce nelokalizované**

   Platí pro aplikace, které vytvářejí dokumenty uživatele. Uživatelé mohli otevřít, vytisknout a uložit dokumenty snadněji, pokud zadáte příponu a ID typu souboru. Tyto položky nejsou lokalizovány, protože jsou použity v systému, nikoli podle uživatele.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Přípona souboru**|Nastaví přípona souboru spojené s dokumenty, které uživatel uloží při používání aplikace. Například pokud váš projekt je název widgetu, třeba mohla mít název za soubor příponu zvolit. (Když zadáte příponu souboru, ne obsahovat tečku.)<br /><br /> Pokud zadáte příponu souboru, můžete v Průzkumníku tisk dokumentů aplikace bez spuštění aplikace, když uživatel na ikonu dokumentu na ikonu tiskárny.<br /><br /> Pokud nezadáte rozšíření, musí uživatel specifikovat příponu souboru při ukládání souborů. Průvodce neposkytuje výchozí příponu souboru.|  
   |**ID typu souboru**|Nastaví název typu dokumentu v systémovém registru.|  
  
- **Lokalizované řetězce**

   Vytváří řetězce, které jsou přidružené k aplikaci a dokument, který se číst a používat uživatelů aplikace.  
  
   |Možnost|Popis|  
   |------------|-----------------|  
   |**Jazyk**|Určuje jazyk, ve kterém jsou zobrazeny řetězce pro všechna pole v **lokalizované řetězce**. Chcete-li změnit hodnotu v tomto poli, vyberte příslušný jazyk v rámci **jazyk prostředku** v [typ aplikace](../../mfc/reference/application-type-mfc-application-wizard.md) stránky Průvodce aplikací knihovny MFC.|  
   |**Titulek hlavního rámce**|Nastaví text zobrazený v horní části hlavního rámce aplikace. Ve výchozím nastavení název projektu.|  
   |**Název typu dokumentu**|Určuje typ dokumentu, pod kterým mohou být seskupeny dokumentu aplikace. Ve výchozím nastavení název projektu. Změna výchozího další možnosti v tomto dialogovém nezmění.|  
   |**Název filtru**|Nastaví název, který mohou uživatelé použít k vyhledání souborů typu souboru. Tato možnost je k dispozici **soubory typu** a **uložit jako typ** možnosti v standardní Windows **otevřít** a **uložit jako** dialogových oknech. Ve výchozím nastavení název projektu a soubory, za nímž následuje rozšíření podle **příponu souboru**. Například, pokud váš projekt má název widgetu a přípona souboru je **název filtru** soubory Widget (*.wgt) je ve výchozím nastavení.|  
   |**Nový krátký název souboru**|Nastaví název zobrazovaný v standardní Windows **nový** dialogové okno, pokud existuje více než jednu šablonu dokumentu. Pokud je vaše aplikace [automatizační server](../../mfc/automation-servers.md), tento název se používá jako krátký název objektu automatizace. Ve výchozím nastavení název projektu.|  
   |**Dlouhý název typu souboru**|Nastaví název typu souboru v systémovém registru. Pokud vaše aplikace je automatizační server, tento název se používá jako dlouhý název objektu automatizace. Ve výchozím nastavení název projektu a. Dokument.|  
  
## <a name="see-also"></a>Viz také  
 [MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

