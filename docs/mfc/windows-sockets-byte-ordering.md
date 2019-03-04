---
title: 'Windows Sockets: Pořadí bajtů'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: ca572ad32a9a46756cacf0221d80b2953b710723
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278090"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Pořadí bajtů

V tomto článku a dva doprovodné články popisují několik problémů v programování v rozhraní Windows Sockets. Tento článek se týká pořadí bajtů. Tyto problémy jsou popsané v článcích: [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md) a [rozhraní Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md).

Pokud používáte nebo odvozen od třídy [CAsyncSocket](../mfc/reference/casyncsocket-class.md), budete muset spravovat tyto problémy sami. Pokud používáte nebo odvozen od třídy [csocket –](../mfc/reference/csocket-class.md), knihovna MFC je spravuje za vás.

## <a name="byte-ordering"></a>Pořadí bajtů

Různou architekturou někdy ukládání dat pomocí různých bajtů objednávky. Například počítače se systémem Intel ukládání dat v obráceném pořadí počítače Macintosh (Motorola). Pořadí bajtů Intel, nazývá "little Endian," je také opakem pořadí síť standardní "big-Endian". Následující tabulka vysvětluje tyto podmínky.

### <a name="big--and-little-endian-byte-ordering"></a>Pořadí bajtů Big - a Little Endian

|Pořadí bajtů|Význam|
|-------------------|-------------|
|Formát Big-Endian|Na levém konci slovo je nejvýznamnější bajt.|
|Ve formátu Little Endian|Na pravém konci slova je nejvýznamnější bajt.|

Obvykle není nutné se starat o převod pořadí bajtů pro data, která můžete odesílat a přijímat přes síť, ale existují situace, ve kterých je nutné převést bajtů objednávky.

## <a name="when-you-must-convert-byte-orders"></a>Když je nutné převést pořadí bajtů

Je potřeba převést bajtů objednávky v následujících situacích:

- Předávání informací, které musí být interpretován sítí, na rozdíl od data, která odesíláte do jiného počítače. Například můžete například předat porty a adresy, které musíte pochopit sítě.

- Serverové aplikace, které budou komunikovat není aplikace knihovny MFC (a nemáte zdrojový kód pro něj). To volá pro převody pořadí bajtů, pokud dva počítače nesdílejí stejné pořadí bajtů.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Pokud není potřeba převést objednávky bajtů

Můžete se vyhnout práci při převádění bajtů objednávek v následujících situacích:

- Počítače na obou koncích můžou dohodnout není na prohození bajtů a oba počítače používají stejné pořadí bajtů.

- Server, které komunikují s je aplikace knihovny MFC.

- Máte zdrojový kód pro server, který komunikujete, takže můžete říct explicitně, jestli musí převést objednávky bajtů nebo ne.

- Můžete port serveru ke knihovně MFC. To je poměrně snadné a výsledkem je obvykle menší a rychlejší kódu.

Práce s [CAsyncSocket](../mfc/reference/casyncsocket-class.md), musí všechny převody potřebné pro pořadí bajtů spravovat sami. Windows Sockets standardizuje modelu "big-Endian" pořadí bajtů a poskytuje funkce pro převod mezi toto pořadí a ostatní. [CArchive](../mfc/reference/carchive-class.md), ale které používáte s [csocket –](../mfc/reference/csocket-class.md), používá opačném pořadí ("little Endian"), ale `CArchive` se postará o podrobnosti převody pořadí bajtů za vás. Pomocí této standardní řazení ve svých aplikacích, nebo pomocí funkce pro převod rozhraní Windows Sockets pořadí bajtů, můžete provést kód větší přenositelnost.

Ideálním případem použití soketů knihovny MFC je, když vytváříte obě strany komunikace: používáte knihovnu MFC na obou koncích. Pokud vytváříte aplikaci, která bude komunikovat s non-MFC aplikací, jako je například FTP server, bude pravděpodobně nutné spravovat vzájemná záměna bajtů sami před předat data do archivu objektu pomocí rozhraní Windows Sockets převodní rutiny **ntohs**, **ntohl**, **htons**, a **htonl**. Příkladem těchto funkcí používaných v komunikaci s aplikací non-MFC se zobrazí později v tomto článku.

> [!NOTE]
>  Při druhém konci komunikace není aplikace knihovny MFC, je také třeba se vyvarovat objektů C++ odvozena z datového proudu `CObject` do archivu vzhledem k tomu, že příjemci nebudou moct jejich zpracování. Přečtěte si poznámku v [rozhraní Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md).

Další informace o objednávkách bajt naleznete v tématu Specifikace rozhraní Windows Sockets k dispozici v sadě Windows SDK.

## <a name="a-byte-order-conversion-example"></a>Příklad převodu pořadí bajtů

Následující příklad ukazuje funkci serializace `CSocket` objekt, který používá archivu. Kromě toho ilustruje použití funkce pro převod pořadí bajtů v rozhraní Windows Sockets API.

V tomto příkladu představuje scénář, ve kterém píšete klienta, který komunikuje s aplikací na non-MFC serveru, pro které nemají přístup ke zdrojovému kódu. V tomto scénáři musíte předpokládat, že server non-MFC používá standardní síťový pořadí bajtů. Naproti tomu klientské aplikace knihovny MFC používá `CArchive` objekt s `CSocket` objektu, a `CArchive` používá pořadí bajtů "little Endian", opak standardní síti.

Předpokládejme, že server non-MFC, se kterým chcete komunikovat má zavedené protokolu pro zprávy paket následujícím postupem:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

V podmínkách knihovny MFC to by být vyjádřena následujícím způsobem:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

V jazyce C++ **struktura** je v podstatě totéž jako třídu. `Message` Struktura může mít členské funkce, jako `Serialize` členské funkce deklarované výše. `Serialize` Členská funkce může vypadat třeba takto:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

Tento příklad příkladu volá pro pořadí bajtů převodů dat, protože došlo k neshodě vymazat mezi pořadí bajtů non-MFC serverovou aplikaci na jednom konci a `CArchive` používaných pro klientské aplikace knihovny MFC na druhém konci. Příklad ukazuje některé funkce pro převod pořadí bajtů, které poskytuje rozhraní Windows Sockets. Následující tabulka popisuje tyto funkce.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets – funkce pro převod pořadí bajtů

|Funkce|Účel|
|--------------|-------------|
|**ntohs**|Převeďte množství 16bitové pořadí bajtů sítě na hostiteli pořadí bajtů (formát big-Endian k little Endian).|
|**ntohl**|Převeďte 32-bit množství pořadí bajtů sítě na hostiteli pořadí bajtů (formát big-Endian k little Endian).|
|**Htons**|Převeďte 16bitové množství z hostitele pořadí bajtů na síťovém pořadí bajtů (little Endian na formát big-Endian).|
|**Htonl**|Převeďte množství 32-bit z hostitele pořadí bajtů na síťovém pořadí bajtů (little Endian na formát big-Endian).|

Jiný bod v tomto příkladu je, že když je aplikace soketu na druhém konci komunikace non-MFC aplikace, můžete musí vyhýbání se dělání přibližně takto:

`ar << pMsg;`

kde `pMsg` je ukazatel na objekt jazyka C++, který je odvozen od třídy `CObject`. Tento tok odešle dodatečné informace MFC související s objekty a server nebude pochopit, jako kdyby byly aplikace knihovny MFC.

Další informace naleznete v tématu:

- [Windows Sockets: Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Background](../mfc/windows-sockets-background.md)

- [Windows Sockets: Stream Sockets](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Sokety datagramu](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
