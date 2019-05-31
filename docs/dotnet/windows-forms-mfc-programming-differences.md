---
title: Windows Forms a MFC programování rozdíly
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 165c72b4f91073947d3914ae773e277cce192564
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449998"
---
# <a name="windows-formsmfc-programming-differences"></a>Rozdíly v programování mezi prostředími Windows Forms a MFC

Témata v [použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) popisovat podporu knihovny MFC pro Windows Forms. Pokud nejste obeznámeni s rozhraní .NET Framework nebo programování knihovny MFC, toto téma obsahuje základní informace o programování rozdíly mezi nimi.

Windows Forms slouží k vytváření aplikací pro Microsoft Windows na rozhraní .NET Framework. Toto rozhraní poskytuje moderní, objektově orientované, rozšiřitelnou sadu tříd, které vám umožní vyvíjet bohaté aplikace pro systém Windows. Pomocí Windows Forms budete moct vytvořit aplikaci rich client, který může přistupovat k širokou škálu zdrojů dat a zobrazení dat a zařízení a úpravy dat pomocí ovládacích prvků Windows Forms.

Ale pokud jste zvyklí ke knihovně MFC, vám dají zneužít k vytvoření určité typy aplikací, které se zatím nepodporují explicitně ve Windows Forms. Aplikace Windows Forms jsou ekvivalentní MFC dialogového okna aplikace. Však neposkytují infrastruktury, které přímo jinými typy aplikací knihovny MFC jako server/kontejner OLE dokumentu, dokumenty ActiveX, Document/View – podpora pro rozhraní jednoho dokumentu (SDI), rozhraní více dokumentů (MDI), a více rozhraní nejvyšší úrovně (MTI). Můžete napsat vlastní logiku k vytváření těchto aplikací.

Další informace o aplikacích pro Windows Forms, naleznete v tématu [Úvod do modelu Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Ukázková aplikace, která ukazuje použití s knihovnou MFC modelu Windows Forms, naleznete v tématu [MFC a integrace formulářů Windows](https://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).

Následující zobrazení MFC nebo dokumentu a příkazu směrování funkce nemají ekvivalent v formuláře Windows:

- Prostředí integrace

   Knihovna MFC zpracovává dynamických dat (DDE) exchange příkazy a argumenty příkazového řádku, které používá prostředí, když klikněte pravým tlačítkem na dokument a vyberte tyto příkazy jako otevřít, upravit nebo vytisknout. Formuláře Windows nemá integraci prostředí a nereaguje na příkazy prostředí.

- Šablony dokumentů

   V knihovně MFC šablony dokumentů přidružit k zobrazení, která je obsažena v okně s rámečkem (v režimu MDI, SDI nebo MTI), dokumentů, které jste otevřeli. Windows Forms nemá žádný ekvivalent k šablony dokumentů.

- Dokumenty

   Knihovna MFC registruje typy souborů dokumentu a zpracovává typ dokumentu, při otevírání dokumentu z prostředí. Windows Forms nemá žádný dokument podpory.

- Stavy dokumentu

   Knihovna MFC udržuje změny stavů pro dokument. Proto při ukončete aplikaci, zavřete poslední zobrazení, která obsahuje aplikaci nebo výstup z Windows, MFC zobrazí výzvu k uložení dokumentů. Windows Forms nemá žádný ekvivalent podpory.

- Příkazy

   Knihovna MFC má koncept příkazy. Řádku nabídek, nástrojů a kontextové nabídky můžete vyvolat všechny stejný příkaz, například vyjmutí a kopírování. Ve Windows Forms příkazy jsou úzce vázané události z konkrétní prvek uživatelského rozhraní (např. položka nabídky); Proto je nutné explicitně připojení všechny události příkazu. Můžete také zpracování více událostí pomocí jedné obslužné rutiny ve Windows Forms. Další informace najdete v tématu [připojení více událostí k jedné obslužné rutině událostí ve Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Směrování příkazů

   Směrování příkazů MFC umožňuje zobrazení aktivního nebo dokument ke zpracování příkazů. Protože ten samý příkaz často mají různý význam pro různá zobrazení (například kopírování chová odlišně v zobrazení pro úpravy textu než v grafickém editoru), příkazy musí být zpracovány aktivní zobrazení. Protože Windows Forms nabídky a panely nástrojů nemají žádné vlastní porozumění aktivního zobrazení, nemůže mít jiné obslužné rutiny pro každý typ zobrazení pro vaše **MenuItem.Click** události bez psaním dalšího kódu, interní.

- Příkaz aktualizační mechanismy

   Knihovna MFC má příkaz Aktualizovat mechanismus. Proto je zodpovědný za stavy prvků UI (například povolování nebo zakazování položka nabídky nebo nástroj tlačítko a zkontrolovat stavy) aktivní zobrazení nebo dokument. Windows Forms nemá žádný ekvivalent mechanismus příkazu update.

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
