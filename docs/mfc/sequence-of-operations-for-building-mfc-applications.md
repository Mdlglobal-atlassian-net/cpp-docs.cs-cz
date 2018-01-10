---
title: "Posloupnost operací při sestavování aplikací MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: applications [MFC], developing
ms.assetid: 6973c714-fe20-48c6-926b-de88356b3a3d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ae1169b438a181e22696502352c19353421469b1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-building-mfc-applications"></a>Posloupnost operací při sestavování aplikací MFC
Následující tabulka popisuje obecné pořadí, které může být obvykle postupujte podle vyvíjet aplikace knihovny MFC.  
  
### <a name="sequence-for-building-an-application-with-the-framework"></a>Pořadí sestavení aplikace pomocí rozhraní  
  
|Úloha|Můžete provést|Nepodporuje rozhraní|  
|----------|------------|------------------------|  
|Vytvoření kostru aplikace.|Spustit [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md). Zadejte požadované možnosti na stránkách možnosti. Mezi možnosti patří vytváření aplikace komponenty modelu COM, kontejneru nebo obojí; Přidání automatizace; a provádění aplikace využívající technologii databáze.|Průvodce aplikací MFC vytvoří soubory kostru aplikace, včetně zdrojových souborů pro aplikace, dokumentu, zobrazení a oken s rámečkem; soubor prostředků; soubor projektu; a jiné, všech podle vašich požadavků.|  
|Zjistěte, co rozhraní a Průvodce aplikací MFC bez přidání řádek vlastní kód.|Sestavení kostru aplikace a spusťte ji v jazyce Visual C++.|Spuštění kostru aplikace odvozuje mnoho standard **soubor**, **upravit**, **zobrazení**, a **pomoci** příkazy nabídky od rozhraní. Pro aplikace MDI získáte také plně funkční nabídky systému Windows a rozhraní spravuje vytváření, uspořádání a odstraňování podřízených oken MDI.|  
|Vytvořte uživatelské rozhraní vaší aplikace.|Pomocí Visual C++ [editory prostředků](../windows/resource-editors.md) vizuálně upravit uživatelské rozhraní aplikace:<br /><br /> -Vytvořte nabídky.<br />-Definujte akcelerátorů.<br />-Vytvořte dialogová okna.<br />-Vytvořit a upravit rastrové obrázky, ikony a kurzory.<br />-Upravte panelu nástrojů pro můžete vytvořit pomocí Průvodce aplikací MFC.<br />-Vytvořit a upravit jiné prostředky.<br /><br /> V editoru dialogového okna můžete také otestovat dialogových oken.|Výchozí soubor prostředků vytvořené průvodcem aplikací MFC poskytuje řadu zdrojů, které potřebujete. Visual C++ umožňuje upravit existující prostředky a přidat nové prostředky snadno a vizuálně.|  
|Mapovat nabídky k funkcím obslužných rutin.|Použití **události** tlačítka na [vlastnosti – okno](/visualstudio/ide/reference/properties-window) připojit nabídek a akcelerátorů k funkcím obslužných rutin ve vašem kódu.|Okno vlastností vloží do zdrojových souborů, zadejte a spravuje mnoho ručních úkonů kódování položek mapy zpráv a funkce prázdné šablony.|  
|Zadejte kód obslužné rutiny.|Pomocí zobrazení tříd přejít přímo na kód v editoru zdrojového kódu. Zadejte kód pro obslužnou rutinu funkcí. Další informace o používání zobrazení tříd a o Průvodci, který přidá do projektu kódu najdete v tématu [přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).|Zobrazení tříd otevře editor, posune funkce prázdné šablonu a umisťuje kurzor pro vás.|  
|Mapování tlačítka panelu nástrojů na příkazy.|Mapování každé tlačítko na panelu nástrojů na příkaz nabídky nebo akcelerátoru přiřazením tlačítko ID příslušný příkaz.|Rozhraní framework řídí kreslení, povolení, zakázání, kontrola a další visual vlastnosti tlačítka panelu nástrojů.|  
|Testování funkce obslužné rutiny.|Znovu sestavte program a použít integrované nástroje pro ladění k testování správné fungování vaší obslužné rutiny.|Můžete krok nebo trasování prostřednictvím kódu, které chcete zobrazit, jak jsou volány vaší obslužné rutiny. Pokud jste vyplnili kód obslužné rutiny, obslužné rutiny provádět příkazy. Rozhraní framework automaticky zakáže položek nabídky a tlačítka panelu nástrojů, které nejsou zpracovány.|  
|Přidat [dialogová okna](../mfc/dialog-boxes.md).|Návrh prostředků šablony dialogového okna pomocí editoru dialogových oken. Pak vytvořte třídy dialogového okna a kód, který zpracovává dialogové okno.|Rozhraní framework spravuje dialogové okno a usnadňuje získávání informací o zadané uživatelem.|  
|Inicializace, ověření a načtení dat – dialogové okno.|Můžete také určit, jak ovládací prvky dialogových oken mají být inicializován a ověřit. Přidání členské proměnné do třídy dialogového okna a jejich namapování na ovládací prvky dialogového okna pomocí sady Visual Studio. Zadejte pravidla ověřování má být použita pro každý ovládací prvek jako uživatel zadá data. Pokud chcete, zadejte vlastní vlastní ověření.|Rozhraní framework spravuje inicializace – dialogové okno a ověření. Pokud uživatel zadá neplatné informace, rozhraní zobrazí okno se zprávou a umožní uživateli zadejte data znovu.|  
|Vytvořte další třídy.|Pomocí zobrazení tříd můžete vytvořit další dokumentu, zobrazení a třídy oken s rámečkem nad rámec těch, automaticky vytvořené průvodcem aplikací MFC. Můžete vytvořit další databázové třídy sady záznamů, třídy dialogových oken a tak dále. (S zobrazení tříd, můžete vytvořit třídy není odvozen od třídy MFC.)|Zobrazení tříd přidá tyto třídy do zdrojových souborů a umožňuje definovat jejich připojení k všechny příkazy, které se budou zpracovávat.|  
|Do aplikace přidáte součásti připravené k použití.|Použití `New Item dialog box` přidat řadu položek.|Tyto položky jsou snadno integrovat do vaší aplikace a ušetřit značnou část práce.|  
|Implementace třídy vašeho dokumentu.|Implementace třídy specifické pro aplikaci dokumentu nebo třídy. Přidání členské proměnné pro uložení datové struktury. Přidání členské funkce účelem poskytnutí rozhraní k datům.|Rozhraní framework již umí interakci s datovými soubory dokumentu. Ho můžete otevřít a zavřete dokument soubory, čtení a zápis data dokumentu a zpracovávat jiné uživatelská rozhraní. Můžete se zaměřit na možností práce s data dokumentu.|  
|Implementace otevření, uložení a uložit jako příkazy.|Psaní kódu pro dokumentu `Serialize` – členská funkce.|Rozhraní zobrazuje dialogová okna pro **otevřete**, **Uložit**, a **uložit jako** příkazy **souboru** nabídky. Zapíše a zpět čte dokumentu s použitím zadané v formát dat vaší `Serialize` – členská funkce.|  
|Implementujte třídě zobrazení.|Implementovat jednu nebo více tříd zobrazení odpovídající dokumentů. Implementujte zobrazení členské funkce, které mapovat na uživatelské rozhraní pomocí zobrazení tříd. Celou řadu [CView](../mfc/reference/cview-class.md)-odvozené třídy jsou k dispozici, včetně [CListView](../mfc/reference/clistview-class.md) a [CTreeView](../mfc/reference/ctreeview-class.md).|Rozhraní framework spravuje většinu vztah mezi dokumentu a jeho zobrazení. Členské funkce zobrazení přístup k dokumentu zobrazení k vykreslení jeho image na tištěných psaných a k aktualizaci dokumentu datové struktury v reakci na uživatel upravující příkazy.|  
|Zvýšit výchozí tisk.|Pokud potřebujete podporovat vícestránkové tisk, potlačí zobrazení členské funkce.|Podporuje rozhraní **tiskových**, **vzhled stránky**, a **Náhled** příkazy **souboru** nabídky. Musí se informování jak rozdělit dokument na více stránkách.|  
|Přidejte posouvání.|Pokud potřebujete podporovat posouvání, odvození třídy zobrazení nebo třídy z [CScrollView](../mfc/reference/cscrollview-class.md).|Zobrazení automaticky přidá posuvníky, když okno zobrazení je příliš malá.|  
|Vytvořte zobrazení formuláře.|Pokud chcete základní zobrazení na prostředcích šablony dialogového okna, odvození třídy zobrazení nebo třídy z [CFormView](../mfc/reference/cformview-class.md).|Zobrazení prostředků šablony dialogového okna používá pro zobrazení ovládacích prvků. Uživatel může kartě z ovládacího prvku na ovládací prvek v zobrazení.|  
|Vytvoření databázových formulářů.|Pokud chcete k aplikaci založené na formulářích přístup k datům, jsou odvozeny třídě zobrazení z [CRecordView](../mfc/reference/crecordview-class.md) (pro programování rozhraní ODBC).|Zobrazení funguje podobně jako zobrazení formuláře, ale jeho ovládací prvky jsou připojeny k pole [CRecordset](../mfc/reference/crecordset-class.md) objekt reprezentující databázové tabulky. MFC přesouvá data mezi ovládacími prvky a sady záznamů za vás.|  
|Vytvoří jednoduchý textový editor.|Pokud chcete, aby zobrazení, aby bylo jednoduchý textový editor, odvození třídy zobrazení nebo třídy z [CEditView](../mfc/reference/ceditview-class.md) nebo [cricheditview –](../mfc/reference/cricheditview-class.md).|Zobrazení obsahuje úpravy souborů vstupu a výstupu, podpora schránky a funkce. `CRichEditView`poskytuje stylem text.|  
|Přidejte rozdělovače oken.|Pokud chcete podporovat rozdělení oken, přidat [CSplitterWnd](../mfc/reference/csplitterwnd-class.md) do oken s rámečkem SDI nebo podřízeného okna MDI objektu a propojte ho v okně nástroje [OnCreateClient](../mfc/reference/cframewnd-class.md#oncreateclient) – členská funkce.|Rozhraní framework poskytuje rozdělovač – ovládací prvky vedle posuvníky a spravuje rozdělit do několika podokna zobrazení. Pokud uživatel rozdělí okno, rozhraní framework vytvoří a připojí další zobrazit objekty v dokumentu.|  
|Vytvoření, testování a ladění aplikace.|Použijte zařízení pro Visual c++ pro vytvoření, testování a ladění aplikace.|Visual C++ umožňuje nastavit kompilace, odkaz a další možnosti. To také umožňuje procházet zdrojový kód a třída struktury.|  
  
## <a name="see-also"></a>Viz také  
 [Posloupnost operací při vytváření aplikací OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Posloupnost operací při vytváření ovládacích prvků ActiveX](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [Posloupnost operací při vytváření databázových aplikací](../mfc/sequence-of-operations-for-creating-database-applications.md)   
 [Sestavení na základě rozhraní .NET Framework](../mfc/building-on-the-framework.md)

