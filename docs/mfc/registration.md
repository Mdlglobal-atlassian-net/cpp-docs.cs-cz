---
title: Registrace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 636a0c2ff254957724511a067fa64533cb4837aa
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="registration"></a>Registrace
Pokud chce uživatel OLE položku vložit do aplikace, uvede OLE typy objektů můžete vybrat ze seznamu. OLE získá tento seznam z registrační databáze systému, který obsahuje informace, které poskytuje všechny serverové aplikace. Když server registruje, položky, které se uloží do databáze systému registrace (registr) popisují každý typ objektu, který poskytne, soubor rozšíření a cestu sama na sebe, mimo jiné informace o.  
  
 Rozhraní framework a OLE systému dynamické knihovny (DLL) použijte tuto registru Pokud chcete zjistit, jaké typy OLE – položky jsou k dispozici v systému. Systém OLE používat knihovny DLL i tato registru určit, jak spuštění serverové aplikace, když je aktivován propojený nebo vložený objekt.  
  
 Tento článek popisuje, co každý server aplikace musí udělat, když je nainstalovaná a pokaždé, když se spustí.  
  
 Podrobné informace o systémovou databázi registrace a formát souboru .reg používat k aktualizaci, najdete v článku *OLE referenční informace pro programátory*.  
  
##  <a name="_core_server_installation"></a>Instalace serveru  
 Při první instalaci aplikace server, se musí zaregistrovat všechny typy položek OLE, které podporuje. Můžete taky nechat serveru aktualizovat systémové databáze registrace pokaždé, když ji spustí jako samostatné aplikace. Díky tomu registrační databáze aktuální Pokud se přesune spustitelný soubor serveru.  
  
> [!NOTE]
>  Aplikace MFC generované průvodcem aplikace automaticky zaregistrovat při spuštění jako samostatné aplikace.  
  
 Pokud chcete pro registraci aplikace během instalace, použijte RegEdit.exe program. Pokud zahrnete instalačního programu s vaší aplikací, mají instalační program spustit "RegEdit /S *appname*.reg". (Příznak /S Určuje tichou operace, tedy nezobrazuje dialogu reporting úspěšné dokončení příkazu.) Jinak vyzvat uživatele k spuštění RegEdit ručně.  
  
> [!NOTE]
>  Soubor .reg vytvořený pomocí Průvodce aplikací neobsahuje úplnou cestu pro tento spustitelný soubor. Instalační program musí buď upravit soubor .reg zahrnout úplná cesta ke spustitelnému souboru nebo změnit proměnné prostředí PATH zahrnout instalační adresář.  
  
 RegEdit sloučí obsah textový soubor .reg registrační databáze. Ověření databázi nebo ji opravit, pomocí Editoru registru. Postará neodstraňujte nezbytné položky OLE.  
  
##  <a name="_core_server_initialization"></a>Inicializace serveru  
 Když vytvoříte aplikaci server pomocí Průvodce aplikací, průvodce dokončí všechny úlohy inicializace pro vás automaticky. Tato část popisuje, co musíte udělat ručně zápisu serverová aplikace.  
  
 Při spuštění aplikace server aplikace kontejneru OLE systémové knihovny DLL přidáním možnost "/ vnoření" na serveru příkazový řádek. Aplikace serveru chování se liší v závislosti na tom, jestli ho byl spuštěn kontejner, takže první věc, kterou by aplikace měla provést při jeho spuštění se kontrola "/ vnoření" nebo "-vkládání objektů" možnost na příkazovém řádku. Pokud existuje tento přepínač, načíst jinou sadu prostředků, které se zobrazí server jako aktivní buď místní nebo plně otevřít. Další informace najdete v tématu [nabídky a prostředky: serverové doplňky](../mfc/menus-and-resources-server-additions.md).  
  
 Aplikace serveru by měly volat také jeho `CWinApp::RunEmbedded` funkce analyzovat příkazového řádku. Pokud vrátí nenulovou hodnotu, aplikace by neměla zobrazit její okno, protože byla spuštěna z aplikace kontejneru, nikoli jako samostatné aplikace. Tato funkce aktualizuje záznam serveru v systému registrační databáze a volání `RegisterAll` – členská funkce pro vás, provedení registrace instance.  
  
 Během spouštění vaše serverová aplikace, je nutné zajistit, aby mohl vykonávat instance registrace. Registrace instance informuje OLE systémové knihovny DLL, že server je aktivní a připravené k přijímání požadavků z kontejnerů. Nepřidává žádné další položku k databázi registrace. Proveďte registraci instance serveru při volání `ConnectTemplate` – členská funkce definované `COleTemplateServer`. To připojí `CDocTemplate` do objektu `COleTemplateServer` objektu.  
  
 `ConnectTemplate` Funkce přijímá tři parametry: serveru **CLSID**, ukazatel `CDocTemplate` objekt a příznak označující, zda server podporuje víc instancí. Miniserver musí být schopné podporovat více instancí, to znamená, musí být možné více instancí serveru můžou běžet současně, jednu pro každý kontejner. V důsledku toho předat **TRUE** pro tento příznak při spuštění miniserver.  
  
 Pokud píšete miniserver, podle definice ho bude vždy spustit kontejner. Stále měli analyzovat příkazového řádku zkontrolujte možnost "/ vnoření". Absence této možnosti na příkazovém řádku znamená, že má uživatel pokusu o spuštění miniserver jako samostatné aplikace. Pokud k tomu dojde, registrace serveru u systémové databáze registrace a pak zobrazit okno se zprávou informující uživatele ke spuštění miniserver z kontejneru aplikace.  
  
## <a name="see-also"></a>Viz také  
 [OLE](../mfc/ole-in-mfc.md)   
 [Servers](../mfc/servers.md)   
 [CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)   
 [CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)   
 [COleTemplateServer – třída](../mfc/reference/coletemplateserver-class.md)
