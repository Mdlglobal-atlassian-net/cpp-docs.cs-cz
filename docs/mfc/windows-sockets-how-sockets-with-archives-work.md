---
title: 'Windows Sockets: Jak pracují sokety s archivy'
ms.date: 11/19/2018
helpviewer_keywords:
- Windows Sockets [MFC], synchronous
- sockets [MFC], synchronous operation
- sockets [MFC], with archives
- synchronous state socket
- Windows Sockets [MFC], with archives
- two-state socket object
ms.assetid: d8ae4039-391d-44f0-a19b-558817affcbb
ms.openlocfilehash: 3af94bc881276238f1a8d2dbeeee4dca1f173a4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389444"
---
# <a name="windows-sockets-how-sockets-with-archives-work"></a>Windows Sockets: Jak pracují sokety s archivy

Tento článek vysvětluje, jak [csocket –](../mfc/reference/csocket-class.md) objektu, [csocketfile –](../mfc/reference/csocketfile-class.md) objektu a [CArchive](../mfc/reference/carchive-class.md) objektu jsou sloučeny pro zjednodušení odesílání a přijímání dat prostřednictvím Windows Soket.

Tento článek [rozhraní Windows Sockets: Příklad Sockets pomocí archivy](../mfc/windows-sockets-example-of-sockets-using-archives.md) uvede `PacketSerialize` funkce. Objekt archiv v `PacketSerialize` příklad funguje stejně jako archiv objekt předaný do knihovny MFC [serializace](../mfc/reference/cobject-class.md#serialize) funkce. Základní rozdíl je, že soketů, archivu je přiřazena není standardní [cfile –](../mfc/reference/cfile-class.md) objektu (obvykle přidružené k souboru na disku) ale položky `CSocketFile` objektu. Místo připojování k souboru na disku, `CSocketFile` objekt připojí k `CSocket` objektu.

A `CArchive` objekt spravuje vyrovnávací paměti. Po zaplnění vyrovnávací paměti ukládání archivu (odesílání), přidružené `CFile` objekt zapíše do vyrovnávací paměti obsahu. Vyprazdňování vyrovnávací paměti archiv připojený soket je ekvivalentní k odeslání zprávy. Po zaplnění vyrovnávací paměti načtení (přijímání) archivu `CFile` objekt zastaví čtení až do vyrovnávací paměti je opět k dispozici.

Třídy `CSocketFile` je odvozena z `CFile`, ale nepodporuje [cfile –](../mfc/reference/cfile-class.md) členské funkce, jako je například funkce polohování (`Seek`, `GetLength`, `SetLength`, a tak dále), uzamčení funguje () `LockRange`, `UnlockRange`), nebo `GetPosition` funkce. Všechny [csocketfile –](../mfc/reference/csocketfile-class.md) musíte udělat objektu je zápis nebo čtení sekvence bajtů do nebo z přidruženého `CSocket` objektu. Protože není zahrnut do souboru, operace jako třeba `Seek` a `GetPosition` žádný smysl. `CSocketFile` je odvozen z `CFile`, takže obvykle to by zdědil všechny tyto členské funkce. Pokud tomu chcete zabránit, nepodporovanou `CFile` členské funkce jsou přepsány v `CSocketFile` vyvolávat [cnotsupportedexception –](../mfc/reference/cnotsupportedexception-class.md).

`CSocketFile` Objekt volá člen funkce jeho `CSocket` objekt odesílat nebo přijímat data.

Následující obrázek znázorňuje vztahy mezi těmito objekty na obou stranách komunikace.

![CArchive – csocketfile – a csocket –](../mfc/media/vc38ia1.gif "CArchive csocketfile – a csocket –") <br/>
CArchive – csocketfile – a csocket –

Účelem této zřejmý složitost je vás chrání před nutností správy podrobnosti soketu sami. Vytvoření soketu, souboru a archivu a následným zahájením odesílání nebo přijímání dat vložením do archivu nebo extrahování z archivu. [CArchive –](../mfc/reference/carchive-class.md), [csocketfile –](../mfc/reference/csocketfile-class.md), a [csocket –](../mfc/reference/csocket-class.md) Správa podrobností na pozadí.

A `CSocket` objekt je ve skutečnosti objekt dvou stavů: v některých případech asynchronní (obvykle stavu) a někdy synchronní. V asynchronní stav můžete soketu přijímat asynchronní oznámení z architektury. Nicméně během určité operace, například na příjem nebo odeslání dat soketu se změní na synchronní. To znamená, že soketu obdrží žádné další asynchronní oznámení, dokud se nedokončí synchronní operace. Protože se Přepíná režimy, vám pomůžou, například přibližně takto:

[!code-cpp[NVC_MFCSimpleSocket#2](../mfc/codesnippet/cpp/windows-sockets-how-sockets-with-archives-work_1.cpp)]

Pokud `CSocket` nejsou implementované jako objekt dvou stavů, je možné přijímat další oznámení pro stejný druh událostí během byly zpracování předchozí oznámení. Například se mohou zobrazovat `OnReceive` oznámení při zpracování `OnReceive`. Ve fragmentu kódu výše, extrahování `str` z archivu, které by mohly vést k rekurzi. Přepnutím státy, `CSocket` brání rekurze zabráněním další oznámení. Obecné pravidlo není žádná oznámení v rámci oznámení.

> [!NOTE]
> A `CSocketFile` slouží také jako soubor (omezený) bez `CArchive` objektu. Ve výchozím nastavení `CSocketFile` konstruktoru *bArchiveCompatible* parametr **TRUE**. Určuje, že objekt souboru je pro použití s archivu. Pokud chcete použít soubor objektu bez archiv, předejte **FALSE** v *bArchiveCompatible* parametru.

V režimu "archivu compatible" `CSocketFile` objekt poskytuje lepší výkon a snižuje nebezpečí "zablokování." K zablokování dochází tehdy, jsou čekání na sebe navzájem a odesílající sokety, nebo čeká na běžné prostředek. Tato situace může nastat, pokud `CArchive` objektu ve spolupráci s `CSocketFile` tak, jak to funguje se službou `CFile` objektu. S `CFile`, archivu můžete předpokládat, že pokud obdrží méně bajtů než je požadováno, na konci souboru se dosáhlo. S `CSocketFile`, ale data jsou zprávy na základě; vyrovnávací paměti může obsahovat více zpráv, tak přijímá méně než počet bajtů neznamená konec souboru. Aplikace není v tomto případě blokování, jak se může stát, že se `CFile`, a můžete pokračovat, přečte zprávy z vyrovnávací paměti, dokud vyrovnávací paměť je prázdná. [IsBufferEmpty](../mfc/reference/carchive-class.md#isbufferempty) fungovat v `CArchive` je užitečný pro sledování stavu archivu vyrovnávací paměti v takovém případě.

Další informace najdete v tématu [rozhraní Windows Sockets: Použití soketů s archivy](../mfc/windows-sockets-using-sockets-with-archives.md)

## <a name="see-also"></a>Viz také:

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CObject::Serialize](../mfc/reference/cobject-class.md#serialize)
