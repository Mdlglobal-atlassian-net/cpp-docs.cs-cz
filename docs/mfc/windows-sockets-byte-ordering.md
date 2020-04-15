---
title: 'Windows Sockets: Pořadí bajtů'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371074"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Pořadí bajtů

Tento článek a dva doprovodné články vysvětlují několik problémů v programování windows sockets. Tento článek se zabývá objednáníbajce bajtů. Další problémy jsou popsány v článcích: [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md) a [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Pokud používáte nebo odvodit z třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset spravovat tyto problémy sami. Pokud používáte nebo odvodit z třídy [CSocket](../mfc/reference/csocket-class.md), MFC spravuje je za vás.

## <a name="byte-ordering"></a>Objednání bajtů

Různé architektury počítače někdy ukládají data pomocí různých bajtových objednávek. Například počítače založené na procesoru Intel ukládat data v obráceném pořadí počítačů Macintosh (Motorola). Intel byte pořadí, volal "little-Endian," je také opak emajekčního standardního "big-Endian" pořadí. Následující tabulka vysvětluje tyto pojmy.

### <a name="big--and-little-endian-byte-ordering"></a>Big- a Little-Endian Byte Řazení

|Pořadí bajtů|Význam|
|-------------------|-------------|
|Velký Endian|Nejvýznamnější bajt je na levém konci slova.|
|Malý-Endian|Nejvýznamnější bajt je na pravém konci slova.|

Obvykle se nemusíte starat o převod pořadí bajtů pro data, která odesíláte a přijímáte v síti, ale existují situace, ve kterých je nutné převést objednávky bajtů.

## <a name="when-you-must-convert-byte-orders"></a>Když je nutné převést objednávky bajtů

Pořadí bajtů je třeba převést v následujících situacích:

- Předáváte informace, které musí síť interpretovat, na rozdíl od dat odesílaných do jiného počítače. Můžete například předat porty a adresy, kterým musí síť rozumět.

- Serverová aplikace, se kterou komunikujete, není aplikací knihovny MFC (a nemáte pro ni zdrojový kód). To vyžaduje převody pořadí bajtů, pokud dva počítače nesdílejí stejné pořadí bajtů.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Když není třeba převádět bajtové objednávky

Můžete se vyhnout práci převodu bajtových objednávek v následujících situacích:

- Stroje na obou koncích se mohou dohodnout, že nebudou vyměňovat bajty, a oba počítače používají stejné pořadí bajtů.

- Server, se kterým komunikujete, je aplikace knihovny MFC.

- Máte zdrojový kód pro server, se kterým komunikujete, takže můžete explicitně zjistit, zda je nutné převést objednávky bajtů nebo ne.

- Server můžete přenést do knihovny MFC. To je poměrně snadné a výsledek je obvykle menší, rychlejší kód.

Práce s [CAsyncSocket](../mfc/reference/casyncsocket-class.md), je nutné spravovat všechny potřebné převody pořadí bajtů sami. Windows Sockets standardizuje model "big-Endian" byte pořadí a poskytuje funkce pro převod mezi tímto pořadím a ostatními. [CArchive](../mfc/reference/carchive-class.md), ale, které používáte s [CSocket](../mfc/reference/csocket-class.md), používá opačné ("little-Endian") pořadí, ale `CArchive` postará se o podrobnosti převody bajtpořadí pro vás. Pomocí tohoto standardního řazení ve vašich aplikacích nebo pomocí funkcí převodu pořadí bajtů rozhraní Windows Sockets můžete kód přenositelnější.

Ideálním případem použití soketů knihovny MFC je, když vytváříte obě strany komunikace: používáte knihovnu MFC na obou koncích. Pokud píšete aplikaci, která bude komunikovat s aplikacemi, které nejsou součástí knihovny MFC, například se serverem FTP, budete pravděpodobně muset před předáním dat do objektu archivu spravovat vlastní výměnu bajtů pomocí rutin převodu rozhraní Windows Sockets **ntohs**, **ntohl**, **htons**a **htonl**. Příklad těchto funkcí používaných při komunikaci s aplikací, která není součástí knihovny MFC, se zobrazí dále v tomto článku.

> [!NOTE]
> Pokud druhý konec komunikace není aplikace knihovny MFC, je také nutné se `CObject` vyhnout streamování objektů jazyka C++ odvozených z do archivu, protože přijímač nebude schopen je zpracovat. Podívejte se na poznámku v [části Windows Sockets: Using Sockets with Archives](../mfc/windows-sockets-using-sockets-with-archives.md).

Další informace o objednávkách bajtů naleznete ve specifikaci windows sockets, která je k dispozici v sadě Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Příklad převodu objednavace

Následující příklad ukazuje funkci serializace `CSocket` pro objekt, který používá archiv. Také ilustruje použití funkcí převodu pořadí bajtů v rozhraní API rozhraní Windows Sockets.

Tento příklad představuje scénář, ve kterém píšete klienta, který komunikuje s aplikací serveru mfc, pro které nemáte přístup ke zdrojovému kódu. V tomto scénáři je nutné předpokládat, že server bez knihovny MFC používá standardní pořadí bajtů sítě. Naproti tomu klientská aplikace knihovny MFC používá `CArchive` objekt s objektem `CSocket` a `CArchive` používá pořadí bajtů "little-Endian", opak síťového standardu.

Předpokládejme, že server, se kterým plánujete komunikovat, má zavedený protokol pro paket zprávy, jako je následující:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

Z hlediska knihovny MFC by to bylo vyjádřeno takto:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

V **jazyce** C++ je struktura v podstatě totéž jako třída. Struktura `Message` může mít členské funkce, `Serialize` jako je například výše deklarovaná členská funkce. Členská `Serialize` funkce může vypadat takto:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Tento příklad vyžaduje převody dat v pořadí bajtů, protože existuje jasná neshoda mezi pořadíbajtů mezi `CArchive` serverovou aplikací bez knihovny MFC na jednom konci a použitým v klientské aplikaci knihovny MFC na druhém konci. Příklad ilustruje několik funkcí převodu pořadí bajtů, které poskytuje aplikace Windows Sockets. Následující tabulka popisuje tyto funkce.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Funkce převodu bajtů v systému Windows

|Funkce|Účel|
|--------------|-------------|
|**ntohs**|Převeďte 16bitové množství z pořadí bajtů sítě na pořadí bajtů hostitele (big-Endian na little-Endian).|
|**ntohl (NTOHL)**|Převod 32bitového množství z pořadí bajtů sítě na pořadí bajtů hostitele (big-Endian na little-Endian).|
|**Htons**|Převeďte 16bitové množství z pořadí bajtů hostitele na pořadí bajtů v síti (little-Endian na big-Endian).|
|**Htonl**|Převést 32bitové množství z pořadí bajtů hostitele na pořadí bajtů sítě (little-Endian na big-Endian).|

Dalším bodem tohoto příkladu je, že když aplikace soketu na druhém konci komunikace je aplikace bez knihovny MFC, je třeba se vyhnout dělat něco jako následující:

`ar << pMsg;`

kde `pMsg` je ukazatel na c++ objekt `CObject`odvozený z třídy . Tím se odešlou další informace knihovny MFC přidružené k objektům a server nebude rozumět, jako by tomu bylo v případě, že by se jednalo o aplikaci knihovny MFC.

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Pozadí](../mfc/windows-sockets-background.md)

- [Windows Sockets: Sokety datového proudu](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramů](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
