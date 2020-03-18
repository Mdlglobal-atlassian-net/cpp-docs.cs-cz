---
title: Windows Sockets – použití třídy CAsyncSocket
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 3977308776c4ec6fed844038c4453ad03d065f98
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445937"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets – použití třídy CAsyncSocket

Tento článek vysvětluje, jak používat třídu [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Upozorňujeme, že tato třída zapouzdřuje rozhraní Windows Sockets API na velmi nízké úrovni. `CAsyncSocket` slouží programátorům, kteří podrobněji znají síťovou komunikaci, ale chtějí rádiová volání pro oznamování událostí sítě. V závislosti na tomto předpokladu poskytuje tento článek pouze základní pokyny. Je vhodné zvážit použití `CAsyncSocket`, pokud chcete, aby rozhraní Windows Sockets bylo snadné řešit více síťových protokolů v aplikaci knihovny MFC, ale nechcete zabývat flexibility. Můžete se také setkat s tím, že můžete dosáhnout lepší efektivity tím, že budete komunikaci naprogramovat přímo, než můžete použít obecnější alternativní model `CSocket`třídy.

`CAsyncSocket` je dokumentován v *Referenci knihovny MFC*. Vizuál C++ také poskytuje specifikaci rozhraní Windows Sockets, která se nachází v Windows SDK. Podrobnosti jsou ponechány na vás. Vizuál C++ neposkytuje ukázkovou aplikaci pro `CAsyncSocket`.

Pokud nemůžete mít vysokou znalost síťové komunikace a chcete použít jednoduché řešení, použijte třídu [CSocket –](../mfc/reference/csocket-class.md) s objektem `CArchive`. Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md) .

Tento článek se týká:

- Vytvoření a použití objektu `CAsyncSocket`.

- [Vaše zodpovědnosti s CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>Vytvoření a použití objektu CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Použití CAsyncSocket

1. Sestavte objekt [CAsyncSocket](../mfc/reference/casyncsocket-class.md) a pomocí objektu vytvořte základní popisovač **soketu** .

   Vytvoření soketu se řídí vzorem knihovny MFC pro konstrukci dvou fází.

   Příklad:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -nebo-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   První konstruktor výše vytvoří objekt `CAsyncSocket` v zásobníku. Druhý konstruktor vytvoří `CAsyncSocket` na haldě. První volání metody [Create](../mfc/reference/casyncsocket-class.md#create) používá výchozí parametry k vytvoření soketu streamu. Druhý `Create` volání vytvoří soket datagram se zadaným portem a adresou. (Můžete použít buď `Create` verze, s metodou konstrukce.)

   Parametry `Create` jsou:

   - "Port": krátké celé číslo.

      U serverového soketu je nutné zadat port. U klientského soketu obvykle přijměte výchozí hodnotu pro tento parametr, což umožňuje rozhraní Windows Sockets vybrat port.

   - Typ soketu: **SOCK_STREAM** (výchozí) nebo **SOCK_DGRAM**.

   - Adresa soketu, například "ftp.microsoft.com" nebo "128.56.22.8".

      Toto je vaše adresa Internet Protocol (IP) v síti. Pro tento parametr se pravděpodobně vždy spoléháte na výchozí hodnotu.

   Pojem "port" a "adresa soketu" jsou vysvětleny v tématu rozhraní [Windows Sockets: porty a adresy soketů](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Pokud je soket klientem, připojte objekt soketu k soketu serveru pomocí [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).

     -nebo-

   Pokud je soket serverem, nastavte soket tak, aby zahájil naslouchání (pomocí [CAsyncSocket:: Listen](../mfc/reference/casyncsocket-class.md#listen)) pro pokusy o připojení od klienta. Po přijetí žádosti o připojení ji přijměte pomocí [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Po přijetí připojení můžete provádět takové úlohy, jako je ověřování hesel.

    > [!NOTE]
    >  Členská funkce `Accept` přebírá odkaz na nový prázdný objekt `CSocket` jako svůj parametr. Tento objekt je nutné vytvořit před voláním `Accept`. Pokud se tento objekt soketu dostane mimo rozsah, připojení se zavře. Nevolejte `Create` pro tento nový objekt soketu. Příklad najdete v článku rozhraní [Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md).

1. Proveďte komunikaci s jinými sokety voláním členských funkcí objektu `CAsyncSocket`, které zapouzdřují funkce rozhraní API Windows Sockets.

   Viz specifikace rozhraní Windows Sockets a třída [CAsyncSocket](../mfc/reference/casyncsocket-class.md) v *Referenci knihovny MFC*.

1. Zničit objekt `CAsyncSocket`.

   Pokud jste vytvořili objekt soketu v zásobníku, jeho destruktor se zavolá, když se nadřazená funkce dostane mimo rozsah. Pokud jste vytvořili objekt soketu na haldě pomocí operátoru **New** , zodpovídáte za použití operátoru **Delete** k zničení objektu.

   Destruktor volá členskou funkci objektu [Close](../mfc/reference/casyncsocket-class.md#close) před zničením objektu.

Příklad této sekvence v kódu (ve skutečnosti pro objekt `CSocket`) najdete v tématu rozhraní [Windows Sockets: posloupnost operací](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a>Vaše zodpovědnosti s CAsyncSocket

Při vytváření objektu třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md)objekt zapouzdřuje popisovač **soketu** systému Windows a dodává operace s tímto popisovačem. Při použití `CAsyncSocket`se musíte vypořádat se všemi problémy, které byste mohli při přímém používání rozhraní API využít. Příklad:

- "Blokující" scénáře.

- Rozdíly v pořadí bajtů mezi odesílajícími a přijímajícími počítači.

- Převod mezi řetězci Unicode a vícebajtové znakové sady (MBCS).

Definice těchto termínů a další informace najdete v tématu [Windows Sockets: blokování](../mfc/windows-sockets-blocking.md), [Windows Sockets: pořadí bajtů](../mfc/windows-sockets-byte-ordering.md), [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md).

Bez ohledu na tyto problémy může být třída `CAsycnSocket` správnou volbou, pokud vaše aplikace vyžaduje veškerou flexibilitu a kontrolu, které můžete získat. V takovém případě byste měli zvážit použití `CSocket` třídy. `CSocket` skrývá mnoho podrobností od vás: pumpuje zprávy systému Windows během blokujících volání a poskytuje přístup k `CArchive`, který spravuje rozdíly v pořadí bajtů a převod řetězce za vás.

Další informace naleznete v tématu:

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety streamu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
