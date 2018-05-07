---
title: 'Nabídky a prostředky: sloučení nabídky | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 252619872fc53e06629a4cbded7e3640131dc94a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="menus-and-resources-menu-merging"></a>Nabídky a prostředky: Sloučení nabídky
Tento článek podrobně popisuje kroky potřebné pro OLE – aplikace dokumentů pro úpravy s náhledem zpracování a aktivace na místě správně. Aktivace na místě představuje výzvu pro kontejner a server (součást) aplikace. Uživatel zůstane ve stejném okně s rámečkem (v rámci kontejneru dokumentu), ale je ve skutečnosti spuštěna jiná aplikace (server). To vyžaduje spolupráce mezi prostředky kontejneru a serverové aplikace.  
  
 Témata popsaná v tomto článku:  
  
- [Rozložení nabídek](#_core_menu_layouts)  
  
- [Panely nástrojů a stavové řádky](#_core_toolbars_and_status_bars)  
  
##  <a name="_core_menu_layouts"></a> Rozložení nabídek  
 Prvním krokem je koordinace rozložení nabídek. Další informace najdete v tématu **vytvoření nabídky** kapitoly [nabídky programování aspekty](https://msdn.microsoft.com/library/ms647557.aspx) ve Windows SDK.  
  
 Aplikace typu kontejner měli vytvořit nové nabídky, který se má použít jenom v případě, že jsou zavedené Aktivované vložené položky. Minimálně by měla obsahovat této nabídky následující kroky v uvedeném pořadí:  
  
1.  Nabídka Soubor je stejný jako ten, který používá, když jsou otevřené soubory. (Obvykle žádné další položky nabídky jsou umístěny před další položky.)  
  
2.  Dva po sobě jdoucí oddělovače.  
  
3.  Okno nabídky stejný jako ten, který používá, když jsou otevřené soubory (jenom Pokud kontejnerové aplikace v aplikaci MDI). Některé aplikace mohou mít jiné nabídky, například možnosti nabídky, které patří v této skupině, která zůstává v nabídce, pokud je aktivován vložené položky na místě.  
  
    > [!NOTE]
    >  Můžou existovat jiné nabídky, které ovlivňují zobrazení dokumentu kontejneru, například přiblížení. Tyto nabídky kontejner se zobrazí mezi dva oddělovače v této nabídce prostředku.  
  
 Aplikace serveru (součást) by měl taky vytvořit nové nabídky speciálně pro aktivace na místě. Mělo by být podobně jako v nabídce použít, když jsou otevřené soubory, ale bez položky nabídky, jako je například soubor a okno, které manipulaci s dokumentu namísto data na serveru. Tato nabídka obvykle se skládá z následujících akcí:  
  
1.  Upravte nabídku stejný jako ten, který používá, když jsou otevřené soubory.  
  
2.  Oddělovač.  
  
3.  Upravování nabídky, jako je například pera nabídky v ukázkové aplikaci Scribble objektu.  
  
4.  Oddělovač.  
  
5.  Nabídka Nápověda.  
  
 Příklad podívejte se na rozložení některé ukázkové místní nabídky pro kontejner a server. Podrobnosti o každé položky nabídky se odebraly aby příklad srozumitelnější. V místní nabídce kontejneru má následující položky:  
  
```  
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&File C1"  
    MENUITEM SEPARATOR  
    POPUP "&Zoom C2"  
    MENUITEM SEPARATOR  
    POPUP "&Options C3"  
    POPUP "&Window C3"  
END  
```  
  
 Po sobě jdoucích oddělovačů uveďte, kde by měli první část serveru nabídky přejít. Podívejte se teď na serveru v místní nabídce:  
  
```  
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE   
BEGIN  
    POPUP "&Edit S1"  
    MENUITEM SEPARATOR  
    POPUP "&Format S2"  
    MENUITEM SEPARATOR  
    POPUP "&Help S3"  
END  
```  
  
 Oddělovače zde indikovat, kde by měli přejít druhé skupině položek nabídky kontejneru. Výsledná struktura nabídky při aktivaci objektu z tohoto serveru na místě uvnitř tohoto kontejneru vypadá takto:  
  
```  
BEGIN  
    POPUP "&File C1"  
    POPUP "&Edit S1"  
    POPUP "&Zoom C2"  
    POPUP "&Format S2"  
    POPUP "&Options C3  
    POPUP "&Window C3"  
    POPUP "&Help S3"  
END  
```  
  
 Jak vidíte, oddělovače nahradil pro různé skupiny nabídky každou aplikaci.  
  
 Tabulky akcelerátoru přidružené v místní nabídce by měl být uveden také aplikací serveru. Kontejner je začlenit do svých tabulek akcelerátorů.  
  
 Pokud je aktivován vložené položky na místě, načte rozhraní v místní nabídce. Potom požádá server aplikaci pro jeho nabídky aktivace na místě a vloží je kde jsou oddělovače. Toto je, jak v nabídkách sloučit. Získat nabídky z kontejneru pro provoz na umístění souboru a okna a získat nabídky ze serveru pro položku.  
  
##  <a name="_core_toolbars_and_status_bars"></a> Panely nástrojů a stavové řádky  
 Aplikace serveru by měl vytvořit nový panel nástrojů a uložení jeho rastrový obrázek v samostatném souboru. Aplikace generované v Průvodci aplikací uložit tento rastrový obrázek v souboru s názvem ITOOLBAR. BMP. Nový panel nástrojů nahradí panel nástrojů aplikace typu kontejner, pokud váš server položku se aktivuje na místě a musí obsahovat stejné položky jako normální panelu nástrojů, ale odebrat ikony představující položky v souboru a oken nabídkách.  
  
 Tento panel nástrojů je načten do vaší `COleIPFrameWnd`-odvozené třídy, můžete vytvořit pomocí Průvodce aplikací. Stavový řádek zpracovává kontejnerové aplikace. Další informace o provádění okna s rámečkem na místě najdete v tématu [servery: implementace serveru](../mfc/servers-implementing-a-server.md).  
  
## <a name="see-also"></a>Viz také  
 [Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)   
 [Aktivace](../mfc/activation-cpp.md)   
 [Servery](../mfc/servers.md)   
 [Kontejnery](../mfc/containers.md)

