---
title: Registrace
ms.date: 11/04/2016
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
ms.openlocfilehash: 0bc606acfba26d27d0ab36045e4772593e760e98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309093"
---
# <a name="registration"></a>Registrace

Když chce uživatel vložení položky OLE do aplikace, OLE zobrazí seznam typů objektů lze vybírat. OLE získá z registrační databázi systému, který obsahuje všechny serverové aplikace na základě informací poskytnutých tohoto seznamu. Když na server se zaregistruje, položky, které se umístí do systému registrační databázi (registr) popisují každý typ objektu, který poskytne, rozšíření a cesta na sebe sama, mimo jiné informace.

Rozhraní framework a OLE systému dynamické knihovny (DLL) použít k určení, jaké typy položek OLE jsou dostupné v systému tohoto registru. OLE systému knihovny DLL také používají tento registr k určení způsobu spuštění serverové aplikace, když se aktivuje objekt propojené nebo vložené.

Tento článek popisuje, co každý server aplikace je potřeba udělat, když je nainstalovaná a pokaždé, když je proveden.

Podrobné informace o systémovou databázi registrace a formátu souboru .reg používat k aktualizaci, najdete v článku *OLE referenční informace pro programátory*.

##  <a name="_core_server_installation"></a> Instalace serveru

Při první instalaci serverové aplikace, měla by ho zaregistrovat všechny typy položek OLE, které podporuje. Můžete taky nechat serveru aktualizovat registraci databáze systému pokaždé, když je spuštěn jako samostatné aplikace. Tím zůstane registrační databázi aktuální Pokud se přesune na server spustitelný soubor.

> [!NOTE]
>  Aplikace MFC generované průvodcem knihovnou aplikace automaticky zaregistrovat při spuštění jako samostatné aplikace.

Pokud chcete zaregistrovat aplikaci během instalace, použití RegEdit.exe programu. Pokud jste instalační program s vaší aplikací, mají instalační program spusťte "RegEdit /S *appname*.reg". (/S příznak určuje tichou operace, to znamená, nezobrazí dialogové okno úspěšné dokončení příkazu.) V opačném případě pokyny pro uživatele, chcete-li spustit program RegEdit ručně.

> [!NOTE]
>  Soubor .reg vytvořený pomocí Průvodce aplikací neobsahuje úplnou cestu pro spustitelný soubor. Instalační program musí buď upravte soubor .reg zahrnout úplnou cestu ke spustitelnému souboru nebo upravit proměnné prostředí PATH zahrnout v instalačním adresáři.

Příkaz RegEdit sloučí obsah textový soubor .reg registrační databázi. Chcete-li ověřit databázi nebo ji opravit pomocí Editoru registru. Snažte se vyhnout odstranění nezbytné položky OLE.

##  <a name="_core_server_initialization"></a> Inicializace serveru

Při vytvoření serverové aplikace pomocí Průvodce aplikací, průvodce dokončí všechny úlohy inicializace pro vás automaticky. Tato část popisuje, co musíte udělat, když zapíšete aplikaci server ručně.

Když je aplikace typu kontejner pro spouštěn serverové aplikace, OLE systémové knihovny DLL přidejte přepínač "/ vkládání" na serveru příkazový řádek. Serverová aplikace chování se liší v závislosti na tom, jestli ho spustila kontejner, tedy první věc, kterou by aplikace měla provést při jeho spuštění vyhledat "/ vkládání" nebo "-obsažení" možnost na příkazovém řádku. Pokud tento přepínač existuje, načíst jinou sadu prostředků, které ukazují server jako aktivní buď místní nebo plně otevřete. Další informace najdete v tématu [nabídky a prostředky: Serverové doplňky](../mfc/menus-and-resources-server-additions.md).

Serverová aplikace byste také zavolat jeho `CWinApp::RunEmbedded` funkci parsování příkazového řádku. Pokud vrátí nenulovou hodnotu, aplikace by neměl zobrazit její okno, protože byl spuštěn z aplikace typu kontejner, ne jako samostatné aplikace. Tato funkce aktualizuje položku serveru v systému registrační databázi a volání `RegisterAll` členskou funkci za vás provádí registraci instance.

Při spuštění vaší serverové aplikace, musíte zajistit, že můžete provádět registraci instance. Registraci instance informuje OLE systémové knihovny DLL, zda je server aktivní a připravena k přijímání požadavků z kontejnerů. Nepřidá položku do registrační databázi. Proveďte registraci instance serveru voláním `ConnectTemplate` členské funkce definované `COleTemplateServer`. To se připojí `CDocTemplate` objektu `COleTemplateServer` objektu.

`ConnectTemplate` Funkce přijímá tři parametry: serveru *CLSID*, ukazatel `CDocTemplate` objektu a příznak označující, zda je server podporuje víc instancí. Miniserver musí být schopni poskytovat podporu více instancí, to znamená, musí být možné pro víc instancí serveru běžet současně, jeden pro každý kontejner. V důsledku toho předat **TRUE** pro tento příznak při spuštění miniserver.

Pokud píšete miniserver, podle definice, které se spustí vždy kontejnerem. By se měly stále analyzovat příkazový řádek ke kontrole možnost "/ vkládání". Neexistence tuto možnost na příkazovém řádku znamená, že uživatel nepokusí spustit miniserver jako samostatné aplikace. Pokud k tomu dojde, server zaregistrujte registrační databázi systému a pak zobrazí okno se zprávou informující uživatele ke spuštění miniserver z aplikace typu kontejner.

## <a name="see-also"></a>Viz také:

[OLE](../mfc/ole-in-mfc.md)<br/>
[Servery](../mfc/servers.md)<br/>
[CWinApp::RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer – třída](../mfc/reference/coletemplateserver-class.md)
