---
title: 'Servery: Implementace oken s rámečkem na místě'
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: bc5439003b7c891ac3f4000c9b7820746aec4c8d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907541"
---
# <a name="servers-implementing-in-place-frame-windows"></a>Servery: Implementace oken s rámečkem na místě

V tomto článku se dozvíte, co musíte udělat, abyste v serverové aplikaci pro vizuální úpravy implementovali okna s rámečkem na místě, pokud nepoužíváte průvodce aplikací k vytvoření serverové aplikace. Místo toho, jak je uvedeno v tomto článku, můžete použít existující třídu místního okna na místě z aplikace vygenerované průvodcem aplikací nebo ukázky dodané s vizuálů C++.

#### <a name="to-declare-an-in-place-frame-window-class"></a>Deklarace třídy vloženého okna na místě

1. Odvodit místní třídu okna s rámečkem z `COleIPFrameWnd`.

   - Použijte makro DECLARE_DYNCREATE v souboru hlaviček třídy.

   - Použijte makro IMPLEMENT_DYNCREATE v souboru implementace třídy (. cpp). To umožňuje, aby objekty této třídy byly vytvořeny rozhraním.

1. Deklarujete `COleResizeBar` člena v třídě okna s rámečkem. To je nutné v případě, že chcete v serverových aplikacích podporovat místní změnu velikosti.

   Deklarujte obslužnou rutinu `Create` `COleResizeBar` [](reference/mfc-class-wizard.md) zprávy(pomocíPrůvodcetřídou)azavolejtesvůjčlen,pokudjstehodefinovali`OnCreate` .

1. Pokud máte panel nástrojů, deklarujte `CToolBar` člena v třídě okna s rámečkem.

   Přepište `OnCreateControlBars` členskou funkci pro vytvoření panelu nástrojů, když je server aktivní. Příklad:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   Podívejte se na diskuzi o tomto kódu podle kroku 5.

1. Do hlavního souboru. cpp zahrňte hlavičkový soubor pro tuto třídu vloženého okna na místě.

1. V `InitInstance` aplikaci pro třídu aplikace `SetServerInfo` zavolejte funkci objektu šablony dokumentu a určete tak prostředky a místní okno rámce, které se použije v otevřených a místních úpravách.

Řada volání funkcí v příkazu **if** vytvoří panel nástrojů z prostředků, které server poskytl. V tomto okamžiku je panel nástrojů součástí hierarchie okna kontejneru. Vzhledem k tomu, že tento `CToolBar`panel nástrojů je odvozen z, předává své zprávy vlastníkovi, oknu rámce aplikace kontejneru, pokud nezměníte vlastníka. To je důvod, proč `SetOwner` je volání nutné. Toto volání změní okno, ve kterém jsou příkazy odesílány jako místní okno rámce serveru, což způsobí, že budou zprávy předány serveru. To umožňuje, aby server reagoval na operace na panelu nástrojů, který poskytuje.

ID rastrového obrázku panelu nástrojů by mělo být stejné jako jiné místní prostředky definované v serverové aplikaci. Zobrazit [nabídky a prostředky: Přidání](../mfc/menus-and-resources-server-additions.md) podrobností o serveru.

Další informace naleznete v tématu [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md)a [CDocTemplate –:: SetServerInfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) v *dokumentaci knihovny tříd*.

## <a name="see-also"></a>Viz také:

[Servery](../mfc/servers.md)<br/>
[Servery: Implementace serveru](../mfc/servers-implementing-a-server.md)<br/>
[Servery: Implementace dokumentů serveru](../mfc/servers-implementing-server-documents.md)<br/>
[Servery: Serverové položky](../mfc/servers-server-items.md)
