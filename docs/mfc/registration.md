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
ms.openlocfilehash: 82411e53620e92eff3484f7d3f7955030fd439ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372832"
---
# <a name="registration"></a>Registrace

Pokud chce uživatel vložit položku OLE do aplikace, ole zobrazí seznam typů objektů, ze kterých si můžete vybrat. OLE získá tento seznam z databáze registrace systému, který obsahuje informace poskytované všechny serverové aplikace. Když se server zaregistruje sám, položky, které vloží do databáze registrace systému (registr) popisují každý typ objektu, který dodává, přípony souborů a cestu k sobě, mimo jiné informace.

Architektura a knihovny dynamických spojnic OLE používají tento registr k určení, jaké typy položek OLE jsou v systému k dispozici. Knihovny DLL systému OLE také používají tento registr k určení způsobu spuštění serverové aplikace při aktivaci propojeného nebo vloženého objektu.

Tento článek popisuje, co musí každá serverová aplikace udělat, když je nainstalována a pokaždé, když je spuštěna.

Podrobné informace o databázi registrace systému a formátu souborů REG použitých k její aktualizaci naleznete v *příručce ole programmer' reference*.

## <a name="server-installation"></a><a name="_core_server_installation"></a>Instalace serveru

Při první instalaci serverové aplikace by měla zaregistrovat všechny typy položek OLE, které podporuje. Server může také aktualizovat databázi registrace systému při každém spuštění jako samostatná aplikace. To udržuje databázi registrace aktuální, pokud je přesunut spustitelný soubor serveru.

> [!NOTE]
> Aplikace knihovny MFC generované průvodcem aplikací se automaticky zaregistrují, když jsou spuštěny jako samostatné aplikace.

Chcete-li během instalace zaregistrovat aplikaci, použijte program RegEdit.exe. Pokud do aplikace zahrnete instalační program, spusťte instalační program "RegEdit /S *appname*.reg". (Příznak /S označuje tichou operaci, to znamená, že nezobrazuje dialogové okno, které hlásí úspěšné dokončení příkazu.) V opačném případě pokyn uživateli spustit RegEdit ručně.

> [!NOTE]
> Soubor REG vytvořený průvodcem aplikací neobsahuje úplnou cestu ke spustitelnému souboru. Instalační program musí buď upravit soubor REG tak, aby zahrnoval úplnou cestu ke spustitelnému souboru, nebo upravit proměnnou prostředí PATH tak, aby zahrnovala instalační adresář.

RegEdit sloučí obsah textového souboru REG do registrační databáze. Chcete-li databázi ověřit nebo opravit, použijte editor registru. Dbát na to, aby se zabránilo odstranění základních položek OLE.

## <a name="server-initialization"></a><a name="_core_server_initialization"></a>Inicializace serveru

Při vytváření serverové aplikace pomocí průvodce aplikací průvodce automaticky dokončí všechny úlohy inicializace. Tato část popisuje, co je nutné provést, pokud napíšete serverovou aplikaci ručně.

Když je serverová aplikace spuštěna kontejnerovou aplikací, knihovny DLL systému OLE přidají možnost "/Embedding" do příkazového řádku serveru. Chování serverové aplikace se liší v závislosti na tom, zda byla spuštěna kontejnerem, takže první věc, kterou by aplikace měla udělat, když začne spouštět, je kontrola možnosti "/Embedding" nebo "-Embedding" na příkazovém řádku. Pokud tento přepínač existuje, načtěte jinou sadu prostředků, které zobrazují server jako aktivní na místě nebo zcela otevřené. Další informace naleznete v [tématu Nabídky a zdroje: Přidání serveru](../mfc/menus-and-resources-server-additions.md).

Serverová aplikace by `CWinApp::RunEmbedded` také měla volat svou funkci k analýzě příkazového řádku. Pokud vrátí nenulovou hodnotu, aplikace by neměla zobrazit své okno, protože byla spuštěna z aplikace kontejneru, nikoli jako samostatná aplikace. Tato funkce aktualizuje položku serveru v databázi `RegisterAll` registrace systému a volá za vás členskou funkci a provádí registraci instance.

Při spuštění serverové aplikace je nutné zajistit, aby mohla provádět registraci instance. Registrace instance informuje knihovny DLL systému OLE, že server je aktivní a připraven přijímat požadavky z kontejnerů. Nepřidá položku do registrační databáze. Proveďte registraci instance serveru `ConnectTemplate` voláním `COleTemplateServer`členské funkce definované společností . Tím se `CDocTemplate` objekt připojí `COleTemplateServer` k objektu.

Funkce `ConnectTemplate` má tři parametry: *server CLSID*, ukazatel `CDocTemplate` na objekt a příznak označující, zda server podporuje více instancí. Miniserver musí být schopen podporovat více instancí, to znamená, že musí být možné pro více instancí serveru spustit současně, jeden pro každý kontejner. V důsledku toho předat **TRUE** pro tento příznak při spuštění miniserveru.

Pokud píšete miniserver, podle definice bude vždy spuštěn kontejnerem. Stále byste měli analyzovat příkazový řádek a zkontrolovat možnost "/Embedding". Absence této možnosti na příkazovém řádku znamená, že se uživatel pokusil spustit miniserver jako samostatnou aplikaci. Pokud k tomu dojde, zaregistrujte server s databází registrace systému a potom zobrazte okno se zprávou informující uživatele o spuštění miniserveru z aplikace kontejneru.

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[Servery](../mfc/servers.md)<br/>
[CWinApp::Spustit automatické](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp::RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[Třída COleTemplateServer](../mfc/reference/coletemplateserver-class.md)
