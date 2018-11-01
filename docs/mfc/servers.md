---
title: Servery
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: d1e0a8ca85055c289d1ef8e1c36fcd35eab61c91
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526498"
---
# <a name="servers"></a>Servery

Aplikace serveru (nebo komponenty aplikace) vytvoří aplikace typu kontejner OLE položky (nebo komponent) pro použití. Vizuální úpravy serverové aplikace také podporuje úpravy s náhledem nebo aktivace na místě. Jiná forma OLE server je [automatizační server](../mfc/automation-servers.md). Některé serverové aplikace podporuje pouze vytváření vložené položky; jiné podporují vytvoření vložené a propojené položky. Některé podporují propojování pouze, i když to není obvyklé. Všechny aplikace server musí podporovat aktivace aplikace typu kontejner, když chce uživatel upravit položku. Aplikace může být kontejner a serverem. Jinými slovy může i začlenění dat do jeho dokumentů a vytvářet data, která mohou být použity jako položky do jiných aplikací dokumentů.

Miniserver je zvláštní druh serverovou aplikaci, která může být spuštěn pouze kontejner. Příkladem miniservers jsou Microsoft Draw a Microsoft Graph. Miniserver nejsou uložené dokumenty jako soubory na disku. Místo toho načte svoje dokumenty z a zapisuje je do položek v dokumentech, které patří do kontejnerů. V důsledku toho miniserver podporuje jenom vkládání není propojování.

Plnou instalaci systému server můžete spustit buď jako samostatné aplikace nebo spustí aplikace typu kontejner. Plnou instalaci systému server může ukládat dokumenty jako soubory na disku. Může podporovat pouze, vkládání, obě vložení a propojení nebo pouze propojení. Uživatel aplikace typu kontejner můžete vytvořit vložená položka. výběrem příkazu Vyjmout nebo kopírovat v serveru a příkaz Paste v kontejneru. Propojená položka je vytvořena výběrem příkazu kopírování na serveru a vložit odkaz v kontejneru. Uživatel můžete případně vytvořit vložené nebo propojené položky pomocí dialogu vložit objekt.

Následující tabulka shrnuje charakteristiky různé typy serverů:

### <a name="server-characteristics"></a>Vlastnosti serveru

|Typ serveru|Podporuje víc instancí|Počet položek na dokument|Dokumenty na instanci|
|--------------------|---------------------------------|------------------------|----------------------------|
|Miniserver|Ano|1|1|
|Úplný server SDI|Ano|1 (Pokud propojení je podporováno, 1 nebo více)|1|
|Úplný server MDI|Ne (není požadováno)|1 (Pokud propojení je podporováno, 1 nebo více)|0 nebo více|

Serverová aplikace by měla podporovat více kontejnerů současně, v případě, že více než jednoho kontejneru se použije k úpravě vložené nebo propojené položky. Pokud je server aplikace SDI (nebo miniserver s rozhraním pole dialogového okna), musí být schopni spustit současně více instancí serveru. To umožňuje samostatnou instanci aplikace pro zpracování konkrétního požadavku kontejneru.

Pokud je server aplikace MDI, ho můžete vytvořit nové podřízené okno MDI pokaždé, když kontejner potřebuje upravovat položky. Tímto způsobem může podporovat jednu instanci aplikace několik kontejnerů.

Serverové aplikace zapotřebí sdělit OLE systémové knihovny DLL, co dělat, když jedna instance serveru je již spuštěn, když se jiný kontejner požaduje jejích služeb: Určuje, zda by měl spustit novou instanci serveru nebo směrovat všechny kontejnery požadavky na jednu instanci Server.

Podrobné informace o serverech najdete v článku:

- [Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)

- [Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md)

- [Servery: Implementace oken s rámečkem na místě](../mfc/servers-implementing-in-place-frame-windows.md)

- [Servery: Serverové položky](../mfc/servers-server-items.md)

- [Servery: Problémy uživatelského rozhraní](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>Viz také

[OLE](../mfc/ole-in-mfc.md)<br/>
[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Pokročilé funkce](../mfc/containers-advanced-features.md)<br/>
[Nabídky a prostředky (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Registrace](../mfc/registration.md)<br/>
[Automatizační servery](../mfc/automation-servers.md)

