---
title: Podpora složených dokumentů, Průvodce aplikací MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.compdoc
ms.assetid: 42e1af83-12c4-438d-92eb-13835afdb148
ms.openlocfilehash: b2ff4f312132b690223f124fd8790d0e2c172b7f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289673"
---
# <a name="compound-document-support-mfc-application-wizard"></a>Podpora složených dokumentů, Průvodce aplikací MFC

Na této stránce Průvodce aplikací MFC určete, jaké úroveň aplikace poskytuje podporu složeného a aktivní dokument. Vaše aplikace musí podporovat document/view – architektura pro podporu složené dokumenty a šablony dokumentů.

Ve výchozím nastavení aplikace obsahuje podporu složeného dokumentu. Pokud přijmete toto výchozí nastavení, aplikace nemůže podporovat aktivní dokumenty nebo složených souborů.

- **Podpora složených dokumentů**

  Určuje, jestli vaše aplikace poskytuje podpora kontejnerů, podporu serveru nebo obojí. Další informace o této oblasti naleznete v tématu:

  - [Kontejnery: Implementace kontejneru](../../mfc/containers-implementing-a-container.md)

  - [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md)

  |Možnost|Popis|
  |------------|-----------------|
  |**Žádné**|Označuje nepodporuje propojování a vkládání (OLE). Ve výchozím nastavení Průvodce aplikací vytvoří aplikace bez podpory ActiveX.|
  |**Kontejner**|Obsahuje propojené a vložené objekty.|
  |**Mini serveru**|Označuje aplikace můžete vytvářet a spravovat objekty složeném dokumentu. Všimněte si, že miniservery nelze spustit samostatně a podporují pouze vložené položky.|
  |**Úplný server**|Označuje aplikace můžete vytvářet a spravovat objekty složeném dokumentu. Úplné servery budou moct spouštět samostatně a podporu propojené i vložené položky.|
  |**Kontejner/úplný server**|Označuje, že aplikace může být kontejner a serverem. Kontejner je aplikace, která můžete začlenit do vlastní dokumenty vložené nebo propojené položky. Server je aplikace, která můžete vytvořit položky automatizace pro použití aplikací typu kontejner.|

- **Další možnosti**

  Označuje, jestli aplikace podporuje aktivní dokumenty. Zobrazit [aktivní dokumenty](../../mfc/active-documents.md) Další informace o této funkci.

  |Možnost|Popis|
  |------------|-----------------|
  |**Server pro aktivní dokument**|Označuje aplikace můžete vytvářet a spravovat aktivní dokumenty. Pokud vyberete tuto možnost, je nutné zadat příponu souboru pro váš server aktivní dokument v **příponu souboru** pole [řetězce šablony dokumentu](../../mfc/reference/document-template-strings-mfc-application-wizard.md) stránky průvodce. Zobrazit [servery pro aktivní dokumenty](../../mfc/active-document-servers.md) Další informace.|
  |**Kontejner pro aktivní dokument**|Označuje, že aplikace může obsahovat aktivní dokumenty v rámci jeho rámce. Aktivní dokumenty mohou zahrnovat například dokumenty aplikace Internet Explorer nebo dokumentů Office, jako je například Microsoft Word soubory nebo tabulky aplikace Excel. Zobrazit [Active Document Containment](../../mfc/active-document-containment.md) Další informace.|
  |**Podpora pro složené soubory**|Aplikace typu kontejner dokumenty ve formátu složeného souboru nejsou serializovány. Tato možnost vynutí načítání celý soubor obsahující objekty do paměti. Přírůstkové uloží pro jednotlivé objekty nejsou k dispozici. Pokud jeden objekt je změněn a následně uložen, jsou uloženy všechny objekty v souboru.|

## <a name="see-also"></a>Viz také:

[MFC – průvodce aplikací](../../mfc/reference/mfc-application-wizard.md)
