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
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371973"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets – použití třídy CAsyncSocket

Tento článek vysvětluje, jak používat třídu [CAsyncSocket](../mfc/reference/casyncsocket-class.md). Uvědomte si, že tato třída zapouzdřuje rozhraní API rozhraní Windows Sockets na velmi nízké úrovni. `CAsyncSocket`je určen pro použití programátory, kteří znají síťovou komunikaci podrobně, ale chtějí pohodlí zpětných volání pro oznámení síťových událostí. Na základě tohoto předpokladu tento článek poskytuje pouze základní instrukce. Pravděpodobně byste měli `CAsyncSocket` zvážit použití, pokud chcete, aby windows sockets 'snadnost práce s více síťových protokolů v aplikaci knihovny MFC, ale nechcete obětovat flexibilitu. Můžete také pocit, že můžete získat lepší efektivitu programováním komunikace přímo sami, `CSocket`než byste mohli použít obecnější alternativní model třídy .

`CAsyncSocket`je dokumentováno v *odkazu knihovny MFC*. Visual C++ také dodává specifikace Windows Sockets, která se nachází v sadě Windows SDK. Podrobnosti jsou ponechány na vás. Visual C++ neposkytuje ukázkovou `CAsyncSocket`aplikaci pro .

Pokud nejste vysoce dobře informovaní o síťové komunikaci a chcete `CArchive` jednoduché řešení, použijte třídu [CSocket](../mfc/reference/csocket-class.md) s objektem. Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives.](../mfc/windows-sockets-using-sockets-with-archives.md)

Tento článek se zabývá:

- Vytváření a `CAsyncSocket` používání objektu.

- [Vaše povinnosti s CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Vytváření a používání objektu CAsyncSocket

#### <a name="to-use-casyncsocket"></a>Použití casyncsocketu

1. Vytvořte objekt [CAsyncSocket](../mfc/reference/casyncsocket-class.md) a použijte objekt k vytvoření základního popisovače **SOCKET.**

   Vytvoření soketu následuje vzor knihovny MFC dvoustupňové konstrukce.

   Příklad:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     -nebo-

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   První konstruktor výše `CAsyncSocket` vytvoří objekt v zásobníku. Druhý konstruktor vytvoří `CAsyncSocket` na haldě. První [create](../mfc/reference/casyncsocket-class.md#create) volání výše používá výchozí parametry k vytvoření soketu datového proudu. Druhé `Create` volání vytvoří soket datagramu se zadaným portem a adresou. (Obě `Create` verze můžete použít s buď metodou konstrukce.)

   Parametry jsou: `Create`

   - "Port": krátké celé číslo.

      Pro soket serveru je nutné zadat port. Pro klientský soket obvykle přijímáte výchozí hodnotu pro tento parametr, který umožňuje windows sockets vybrat port.

   - Typ soketu: **SOCK_STREAM** (výchozí) nebo **SOCK_DGRAM**.

   - Soket "adresa", například "ftp.microsoft.com" nebo "128.56.22.8".

      Toto je adresa vašeho internetového protokolu (IP) v síti. Pravděpodobně budete vždy spoléhat na výchozí hodnotu pro tento parametr.

   Termíny "port" a "socket adresa" jsou vysvětleny v [zásuvky systému Windows: porty a adresy soketu](../mfc/windows-sockets-ports-and-socket-addresses.md).

1. Pokud je soket klientem, připojte objekt soketu k soketu serveru pomocí [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     -nebo-

   Pokud je soket server, nastavte soket začít naslouchat (s [CAsyncSocket::Listen)](../mfc/reference/casyncsocket-class.md#listen)pro pokusy o připojení od klienta. Po obdržení žádosti o připojení jej přijměte pomocí [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Po přijetí připojení můžete provádět takové úkoly, jako je ověřování hesel.

    > [!NOTE]
    >  Členská `Accept` funkce přebírá jako svůj `CSocket` parametr odkaz na nový prázdný objekt. Tento objekt je nutné `Accept`vytvořit před voláním . Pokud tento objekt soketu přejde mimo rozsah, připojení se zavře. Nevolejte `Create` tento nový objekt soketu. Příklad naleznete v článku [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

1. Provádějte komunikaci s `CAsyncSocket` jinými sokety voláním členských funkcí objektu, které zapouzdřují funkce rozhraní API rozhraní API systému Windows Sockets.

   Viz specifikace Windows Sockets a třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md) v *odkazu knihovny MFC*.

1. Zničte `CAsyncSocket` objekt.

   Pokud jste vytvořili objekt soketu v zásobníku, jeho destruktor je volána při obsahující funkce přejde mimo rozsah. Pokud jste vytvořili objekt soketu na haldě, pomocí **nového** operátoru, jste zodpovědní za použití **operátoru delete** zničit objekt.

   Destruktor volá členská funkci [Close](../mfc/reference/casyncsocket-class.md#close) objektu před zničením objektu.

Příklad této sekvence v kódu (ve `CSocket` skutečnosti pro objekt) naleznete v tématu [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Vaše povinnosti s CAsyncSocket

Při vytváření objektu třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md)objekt zapouzdřuje popisovač Windows **SOCKET** a poskytuje operace na tomto popisovači. Při použití `CAsyncSocket`, musíte řešit všechny problémy, kterým může čelit při použití rozhraní API přímo. Příklad:

- "Blokování" scénáře.

- Rozdíly pořadí bajtů mezi odesílajícími a přijímajícími počítači.

- Převod mezi řetězci Unicode a vícebajtové znakové sady (MBCS).

Definice těchto termínů a další informace naleznete [v tématu Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md), Windows [Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Navzdory těmto problémům `CAsycnSocket` může být třída tou správnou volbou, pokud vaše aplikace vyžaduje veškerou flexibilitu a kontrolu, kterou můžete získat. Pokud ne, měli byste `CSocket` zvážit použití třídy místo. `CSocket`skrývá spoustu detailů od vás: to čerpadla Windows zprávy během `CArchive`blokování hovorů a umožňuje přístup k , který spravuje byte pořadí rozdíly a řetězec konverze pro vás.

Další informace naleznete v tématu:

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
