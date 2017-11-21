---
title: "Podpora složených dokumentů, Průvodce aplikací knihovny MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.compdoc
dev_langs: C++
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 952f27b0c6717d23395453e5159e125370a76804
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compound-document-support-mfc-application-wizard"></a>Podpora složených dokumentů, Průvodce aplikací MFC
Na této stránce Průvodce aplikací MFC indikovat, na jakou úroveň aplikace nabízí podporu složeného a aktivní dokument. Aplikace musí podporovat document/view – architektura pro podporu složené dokumenty a šablony dokumentů.  
  
 Ve výchozím nastavení aplikace obsahuje podporu složeného dokumentu. Pokud přijmete toto výchozí nastavení, nemůže aplikace podporovat aktivní dokumenty nebo složené soubory.  
  
 **Podpora složených dokumentů**  
 Určuje, zda aplikace nabízí podporu kontejneru, podpora serveru nebo obojí. Další informace o této oblasti najdete v tématu:  
  
-   [Kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md)  
  
-   [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md)  
  
|Možnost|Popis|  
|------------|-----------------|  
|**None**|Označuje žádná podpora pro propojování a vkládání (OLE). Ve výchozím nastavení vytvoří Průvodce aplikace bez podpory ActiveX.|  
|**Kontejner**|Obsahuje propojené a vložené objekty.|  
|**Mini serveru**|Určuje aplikace, můžete vytvořit a spravovat objekty složeného dokumentu. Všimněte si, že mini servery nelze spustit samostatně a podporují pouze vložené položky.|  
|**Úplný server**|Určuje aplikace, můžete vytvořit a spravovat objekty složeného dokumentu. Úplné servery je možné spouštět samostatně a podporují propojené i vložené položky.|  
|**Kontejner/úplný server**|Označuje, že aplikace může být kontejner i server. Kontejner je aplikace, která může obsahovat vložené nebo propojené položky do svých vlastních dokumentů. Server je aplikace, která můžete vytvořit položky automatizace pro použití aplikace typu kontejner.|  
  
 **Další možnosti**  
 Určuje, jestli aplikace podporuje aktivní dokumenty. V tématu [aktivní dokumenty](../../mfc/active-documents.md) Další informace o této funkci.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Server pro aktivní dokument**|Určuje aplikace, můžete vytvořit a spravovat aktivní dokumenty. Pokud vyberete tuto možnost, musíte zadat příponu souboru pro aktivní dokument server v **příponu souboru** pole [řetězce šablony dokumentu](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stránce průvodce. V tématu [aktivní dokument servery](../../mfc/active-document-servers.md) Další informace.|  
|**Kontejner pro aktivní dokument**|Označuje, že aplikace může obsahovat aktivní dokumenty v rámci jeho rámečku. Aktivní dokumenty může zahrnovat například Internet Explorer dokumenty nebo dokumenty Office například soubory aplikace Microsoft Word nebo tabulky aplikace Excel. V tématu [obsahování pro aktivní dokument](../../mfc/active-document-containment.md) Další informace.|  
|**Podpora pro složené soubory**|Aplikace typu kontejner dokumentů pomocí formát souboru složené nejsou serializovány. Tato možnost způsobí načítání celý soubor obsahující objekty do paměti. Přírůstkové uložení jednotlivých objektů nejsou k dispozici. Pokud se jeden objekt změněn a následně uložen, se uloží všechny objekty v souboru.|  
  
## <a name="see-also"></a>Viz také  
 [MFC – Průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)

