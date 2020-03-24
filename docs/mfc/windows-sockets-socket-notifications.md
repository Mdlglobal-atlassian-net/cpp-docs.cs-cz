---
title: 'Windows Sockets: Oznámení soketů'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167768"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Oznámení soketů

Tento článek popisuje funkce oznámení ve třídách soketu. Tyto členské funkce jsou funkce zpětného volání, které rozhraní volá, aby upozornilo váš objekt soketu o důležitých událostech. Funkce oznámení jsou:

- [Inreceive](../mfc/reference/casyncsocket-class.md#onreceive): upozorní tento soket na to, že data jsou ve vyrovnávací paměti, aby je bylo možné načíst voláním [Receive](../mfc/reference/casyncsocket-class.md#receive).

- [Send](../mfc/reference/casyncsocket-class.md#onsend): upozorní tento soket, že nyní může odesílat data voláním [Send](../mfc/reference/casyncsocket-class.md#send).

- [Přijmout](../mfc/reference/casyncsocket-class.md#onaccept): oznámí tomuto naslouchajícímu soketu, že může přijmout žádosti o připojení nedokončené voláním [Accept](../mfc/reference/casyncsocket-class.md#accept).

- [Connect](../mfc/reference/casyncsocket-class.md#onconnect): oznámí tomuto soketu připojení, že se dokončil pokus o připojení: možná úspěšně nebo možná došlo k chybě.

- [Close](../mfc/reference/casyncsocket-class.md#onclose): upozorní tento soket, že soket, ke kterému je připojen, je uzavřený.

    > [!NOTE]
    >  Další funkcí oznámení je [OnOutOfBandData](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Toto oznámení oznamuje přijímacímu soketu, že odesílající zásuvka má "vzdáleně nacházející" data k odeslání. Data mimo IP síť jsou logicky nezávislý kanál spojený s každou dvojicí soketů připojených datových proudů. Pro posílání "naléhavých" dat se obvykle používá integrovaný kanál. Knihovna MFC podporuje data mimo IP síť. Pokročilí uživatelé, kteří pracují s třídou [CAsyncSocket](../mfc/reference/casyncsocket-class.md) , můžou potřebovat používat mimo IP síť, ale uživatelé třídy [CSocket –](../mfc/reference/csocket-class.md) se nedoporučuje používat. Jednodušším způsobem je vytvořit druhý soket pro předávání těchto dat. Další informace o datech mimo IP síť najdete v tématu specifikace rozhraní Windows Sockets, která je dostupná ve Windows SDK.

Pokud je odvozeno od třídy `CAsyncSocket`, je nutné přepsat funkce oznámení pro tyto události sítě, které mají zájem na vaši aplikaci. Je-li Třída odvozena od třídy `CSocket`, je zvolena bez ohledu na to, jestli chcete přepsat funkce oznámení, které vás zajímají. Můžete také použít `CSocket` sám sebe. v takovém případě funkce oznámení neprovádí žádnou akci.

Tyto funkce jsou přepsatelné funkce zpětného volání. `CAsyncSocket` a `CSocket` převádějí zprávy na oznámení, ale musíte implementovat způsob, jakým funkce oznámení reagují, pokud je chcete použít. Funkce oznámení jsou volány v době, kdy je váš soket upozorněn na událost zájmu, jako je například přítomnost dat ke čtení.

Knihovna MFC volá funkce oznámení, aby bylo možné přizpůsobit chování soketu v okamžiku oznámení. Například můžete volat `Receive` z funkce pro oznamování `OnReceive`, to znamená, že při oznámení, že je potřeba číst data, zavoláte `Receive` pro jeho čtení. Tento přístup není nutný, ale jedná se o platný scénář. Alternativně můžete použít vaši funkci oznámení ke sledování průběhu, tisku **trasovacích** zpráv atd.

Tato oznámení můžete využít přepsáním funkcí oznámení v odvozené třídě soketu a poskytnutím implementace.

Během operace, jako je například přijímání nebo posílání dat, se objekt `CSocket` bude synchronní. Během synchronního stavu se všechna oznámení určená pro jiné sokety zařadí do fronty, zatímco aktuální soket počká na oznámení, které chce. (Například během volání `Receive` vyžaduje soket oznámení ke čtení.) Jakmile soket dokončí svou synchronní operaci a bude znovu asynchronní, ostatní sokety mohou začít přijímat oznámení ve frontě.

> [!NOTE]
> V `CSocket`není funkce oznamování `OnConnect` nikdy volána. U připojení zavoláte `Connect`, které vrátí po dokončení připojení (buď úspěšně, nebo v případě chyby). Jak jsou zpracovávána oznámení o připojení, je podrobnostmi implementace knihovny MFC.

Podrobnosti o jednotlivých funkcích oznámení naleznete v části Class `CAsyncSocket` v *Referenci knihovny MFC*. Zdrojový kód a informace o ukázkách MFC naleznete v tématu [MFC Samples](../overview/visual-cpp-samples.md#mfc-samples).

Další informace naleznete v tématu:

- [Windows Sockets – Použití třídy CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Odvozování z tříd soketů](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Jak pracují sokety s archivy](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Blokování](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Pořadí bajtů](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Převádění řetězců](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Viz také

[Windows Sockets v prostředí MFC](../mfc/windows-sockets-in-mfc.md)
