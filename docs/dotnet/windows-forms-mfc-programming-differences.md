---
title: Model Windows Forms – rozdíly v programování knihovny MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
ms.openlocfilehash: 136549bb457cc17293d4c7201c9836d9094eea94
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965552"
---
# <a name="windows-formsmfc-programming-differences"></a>Rozdíly v programování mezi prostředími Windows Forms a MFC

Témata v tématu [použití uživatelského ovládacího prvku Windows Form v knihovně MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) popisují podporu knihovny mfc pro model Windows Forms. Pokud nejste obeznámeni s programováním .NET Framework nebo MFC, toto téma poskytuje základní informace o rozdílech mezi programováním mezi těmito dvěma.

Model Windows Forms slouží k vytváření aplikací pro Microsoft Windows v .NET Framework. Toto rozhraní poskytuje moderní, objektově orientované a rozšiřitelnou sadu tříd, které vám umožní vyvíjet aplikace pro Windows s využitím. Pomocí model Windows Forms můžete vytvořit bohatou klientskou aplikaci, která bude mít přístup k široké škále zdrojů dat, a poskytuje zařízení pro zobrazení dat a úpravy dat pomocí model Windows Forms ovládacích prvků.

Pokud jste však zvyklí na knihovnu MFC, můžete použít k vytvoření určitých typů aplikací, které ještě nejsou explicitně podporované v model Windows Forms. Aplikace model Windows Forms jsou ekvivalentní k aplikacím MFC dialog. Neposkytují však infrastrukturu pro přímou podporu jiných typů aplikací knihovny MFC, jako je například dokumentový server nebo kontejner technologie OLE, dokumenty ActiveX, dokument/zobrazení, podpora rozhraní SDI (Single-Document Interface), rozhraní více dokumentů (MDI) a více rozhraní na nejvyšší úrovni (MTI). Chcete-li vytvořit tyto aplikace, můžete napsat vlastní logiku.

Další informace o model Windows Formsch aplikacích najdete v tématu [Úvod do model Windows Forms](/dotnet/framework/winforms/windows-forms-overview).

Ukázkovou aplikaci, která zobrazuje model Windows Forms používané v prostředí MFC, naleznete v tématu [integrace MFC a model Windows Forms](https://www.microsoft.com/download/details.aspx?id=2113).

Následující zobrazení knihovny MFC nebo funkce směrování dokumentu a příkazů nemají v model Windows Forms žádné ekvivalenty:

- Integrace prostředí

   Knihovna MFC zpracovává příkazy DDE (Dynamic Data Exchange) a argumenty příkazového řádku, které prostředí používá, když kliknete pravým tlačítkem myši na dokument a vyberete tyto příkazy jako otevřené, úpravy nebo tisk. Model Windows Forms nemá žádnou integraci prostředí a nereaguje na příkazy prostředí.

- Šablony dokumentů

   V knihovně MFC přiřadí šablony dokumentu zobrazení, které je obsaženo v okně rámce (v režimu MDI, SDI nebo MTI), s dokumentem, který jste otevřeli. Model Windows Forms nemá žádný ekvivalent k šablonám dokumentů.

- Dokumenty

   Knihovna MFC registruje typy souborů dokumentů a zpracovává typ dokumentu při otevírání dokumentu z prostředí. Model Windows Forms nemá podporu dokumentu.

- Stavy dokumentů

   Knihovna MFC udržuje v dokumentu nečisté stavy. Proto při zavření aplikace zavře poslední zobrazení, které obsahuje aplikaci, nebo ukončí činnost z Windows, knihovna MFC vás vyzve k uložení dokumentu. Model Windows Forms nemá žádnou ekvivalentní podporu.

- Příkazy

   Knihovna MFC má koncept příkazů. Panel nabídek, panel nástrojů a kontextová nabídka může vyvolat stejný příkaz, například vyjmout a kopírovat. V model Windows Forms jsou příkazy úzce vázané události z konkrétního prvku uživatelského rozhraní (například položky nabídky). Proto je nutné explicitně připojit všechny události příkazu. Můžete také zpracovat více událostí s jednou obslužnou rutinou v model Windows Forms. Další informace naleznete v tématu [připojení více událostí k jedné obslužné rutině události v model Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).

- Směrování příkazů

   Směrování příkazů MFC umožňuje aktivnímu zobrazení nebo dokumentu zpracovat příkazy. Vzhledem k tomu, že stejný příkaz často má různé významy různých zobrazení (například kopírování se chová jinak v zobrazení pro úpravy textu než v grafickém editoru), musí být příkazy zpracovány aktivním zobrazením. Vzhledem k tomu, že model Windows Forms nabídky a panely nástrojů nemají žádné znalosti o aktivním zobrazení, nemůžete mít pro každý typ zobrazení pro položku MenuItem jinou obslužnou rutinu **. klikněte na tlačítko** události bez psaní dalšího interního kódu.

- Mechanismus aktualizace příkazu

   MFC má mechanismus aktualizace příkazu. Proto aktivní zobrazení nebo dokument zodpovídá za stav prvků uživatelského rozhraní (například povolení nebo zakázání položky nabídky nebo tlačítka nástroje a zaškrtnuté stavy). Model Windows Forms nemá žádný ekvivalent mechanismu aktualizace příkazů.

## <a name="see-also"></a>Viz také:

[Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
