---
title: CSocket – třída
ms.date: 11/04/2016
f1_keywords:
- CSocket
- AFXSOCK/CSocket
- AFXSOCK/CSocket::CSocket
- AFXSOCK/CSocket::Attach
- AFXSOCK/CSocket::CancelBlockingCall
- AFXSOCK/CSocket::Create
- AFXSOCK/CSocket::FromHandle
- AFXSOCK/CSocket::IsBlocking
- AFXSOCK/CSocket::OnMessagePending
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
ms.openlocfilehash: 3f0a7a9a90250ede7b112cfbd9bc1ca14d583356
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318196"
---
# <a name="csocket-class"></a>CSocket – třída

Odvozuje `CAsyncSocket`z , dědí jeho zapouzdření rozhraní API rozhraní Windows Sockets a `CAsyncSocket` představuje vyšší úroveň abstrakce než objektu.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Vytvoří `CSocket` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CSocket::Připojit](#attach)|Připojí popisovač SOCKET `CSocket` k objektu.|
|[CSocket::Zrušit blokování volání](#cancelblockingcall)|Zruší blokování volání, které právě probíhá.|
|[CSocket::Vytvořit](#create)|Vytvoří soket.|
|[CSocket::FromHandle](#fromhandle)|Vrátí ukazatel na `CSocket` objekt, daný popisovač SOCKET.|
|[csocket::isblocking](#isblocking)|Určuje, zda probíhá blokující volání.|

### <a name="protected-methods"></a>Chráněné metody

|Name (Název)|Popis|
|----------|-----------------|
|[csocket::OnMessagePending CSocket::OnMessagePending CSocket::OnMessagePending CSocket](#onmessagepending)|Volána ke zpracování čekajících zpráv při čekání na dokončení blokovacího volání.|

## <a name="remarks"></a>Poznámky

`CSocket`pracuje s `CSocketFile` `CArchive` třídami a spravuje odesílání a přijímání dat.

Objekt `CSocket` také poskytuje blokování, což je nezbytné pro `CArchive`synchronní provoz . Blokovací funkce, `Receive` `Send`například `SendTo`, `Accept` `ReceiveFrom`, , `CAsyncSocket`a (všechny `WSAEWOULDBLOCK` zděděné z ) nevracejí chybu v `CSocket`. Místo toho tyto funkce počkejte, dokud nebude operace dokončena. Navíc původní volání bude ukončena s chybou WSAEINTR, pokud `CancelBlockingCall` je volána, zatímco jedna z těchto funkcí blokuje.

Chcete-li `CSocket` použít objekt, volání konstruktoru, pak volání `Create` k vytvoření základní hostoru SOCKET (typ SOCKET). Výchozí parametry `Create` vytvoření soketu datového proudu, ale pokud `CArchive` nepoužíváte soket s objektem, můžete místo toho zadat parametr pro vytvoření soketu datagramu nebo vytvořit vazbu na konkrétní port a vytvořit soket serveru. Připojte se k `Connect` soketu klienta pomocí na straně klienta a `Accept` na straně serveru. Potom vytvořte `CSocketFile` objekt a `CSocket` přidružte jej k objektu v konstruktoru. `CSocketFile` Dále vytvořte `CArchive` objekt pro odesílání a jeden pro příjem dat `CSocketFile` (podle `CArchive` potřeby), pak je přidružte k objektu v konstruktoru. Po dokončení komunikace zničte objekty `CArchive`, `CSocketFile`a `CSocket` objekty. Datový typ SOCKET je popsán v článku [Windows Sockets: Background](../../mfc/windows-sockets-background.md).

Při použití `CArchive` `CSocketFile` s `CSocket`a , může `CSocket::Receive` dojít k situaci, `PumpMessages(FD_READ)`kdy zadá smyčky (podle ) čekání na požadované množství bajtů. Důvodem je, že jsou povoleny pouze jedno `CSocketFile` volání `CSocket` recv na FD_READ oznámení, ale a umožňují více volání recv na FD_READ. Pokud získáte FD_READ, když není žádná data ke čtení, aplikace přestane reagovat. Pokud nikdy získat další FD_READ, aplikace přestane komunikovat přes soket.

Tento problém můžete vyřešit následujícím způsobem. V `OnReceive` metodě socket třídy `CAsyncSocket::IOCtl(FIONREAD, ...)` volání před `Serialize` voláním metody message třídy, když očekávaná data, která mají být přečtena ze soketu překročí velikost jednoho paketu TCP (maximální přenosová jednotka síťového média, obvykle alespoň 1096 bajtů). Pokud je velikost dostupných dat menší, než je potřeba, počkejte na přijetí všech dat a teprve potom spusťte operaci čtení.

V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává, že obdrží. Předpokládá se, že deklarujete ji jinde v kódu.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
> Při použití soketů knihovny MFC v sekundárních vláknech `AfxSocketInit` v staticky propojené aplikaci knihovny MFC je nutné volat v každém vlákně, které používá sokety k inicializaci knihoven soketu. Ve výchozím `AfxSocketInit` nastavení se nazývá pouze v primárním vlákně.

Další informace naleznete [v tématu Windows Sockets in MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: How Sockets with Archives Work](../../mfc/windows-sockets-how-sockets-with-archives-work.md), Windows [Sockets: Sequence of Operations](../../mfc/windows-sockets-sequence-of-operations.md), Windows [Sockets: Example of Sockets Using Archives](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsock.h

## <a name="csocketattach"></a><a name="attach"></a>CSocket::Připojit

Volání této členské funkce `hSocket` připojit `CSocket` popisovač k objektu.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač do soketu.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Popisovač SOCKET je uložen v [datovém](../../mfc/reference/casyncsocket-class.md#m_hsocket) členu m_hSocket objektu.

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

## <a name="csocketcancelblockingcall"></a><a name="cancelblockingcall"></a>CSocket::Zrušit blokování volání

Volání této členské funkce zrušit blokování volání právě probíhá.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Poznámky

Tato funkce zruší všechny nevyřízené blokování operace pro tento soket. Původní blokovací volání bude ukončeno co nejdříve s chybou WSAEINTR.

V případě operace `Connect` blokování implementace Windows Sockets ukončí volání blokování co nejdříve, ale nemusí být možné pro prostředky soketu, které mají být uvolněny, dokud připojení bylo dokončeno (a potom byl reset) nebo vypršel časový limit. To je pravděpodobně patrné pouze v případě, že aplikace okamžitě pokusí otevřít nový soket (pokud nejsou k dispozici žádné sokety) nebo se připojit ke stejnému partnerovi.

Zrušení jakékoli jiné `Accept` operace, než může opustit soket v neurčitém stavu. Pokud aplikace zruší blokovací operaci na soketu, jedinou operací, na které může aplikace `Close`záviset na možnosti provádět na soketu , je volání aplikace , ačkoli jiné operace mohou fungovat v některých implementacích Windows Sockets. Pokud si přejete maximální přenositelnost pro vaši aplikaci, musíte být opatrní, abyste nebyli závislí na provádění operací po zrušení.

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcreate"></a><a name="create"></a>CSocket::Vytvořit

Volání **Vytvořit** členská funkce po vytvoření objektu soketu k vytvoření soketu systému Windows a připojení.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Konkrétní port, který má být použit se soketem, nebo 0, pokud chcete, aby knihovna MFC vybrala port.

*nTyp socket*<br/>
SOCK_STREAM nebo SOCK_DGRAM.

*lpszSocketAddress*<br/>
Ukazatel na řetězec obsahující síťovou adresu připojeného soketu, tečkované číslo, například "128.56.22.8". Předání řetězce NULL pro tento `CSocket` parametr znamená, že instance by měla naslouchat aktivitě klienta ve všech síťových rozhraních.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze `GetLastError`načíst voláním .

### <a name="remarks"></a>Poznámky

`Create`pak `Bind` volá svázat soket na zadanou adresu. Podporovány jsou následující typy soketů:

- SOCK_STREAM Poskytuje sekvenční, spolehlivé, obousměrné, založené na připojení bajtové proudy. Používá protokol TCP (Transmission Control Protocol) pro rodinu internetových adres.

- SOCK_DGRAM Podporuje datagramy, které jsou bezpřipojení, nespolehlivé vyrovnávací paměti pevné (obvykle malé) maximální délky. Používá protokol UDP (User Datagram Protocol) pro rodinu internetových adres. Chcete-li použít tuto možnost, nesmíte `CArchive` používat soket s objektem.

    > [!NOTE]
    >  Členská `Accept` funkce přebírá jako svůj `CSocket` parametr odkaz na nový prázdný objekt. Tento objekt je nutné `Accept`vytvořit před voláním . Mějte na paměti, že pokud tento objekt soketu přejde mimo rozsah, připojení se zavře. Nevolejte `Create` tento nový objekt soketu.

Další informace o soketech datových proudů a datových gramů naleznete v článcích [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: Ports and Socket Addresses](../../mfc/windows-sockets-ports-and-socket-addresses.md) [a Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketcsocket"></a><a name="csocket"></a>CSocket::CSocket

Vytvoří `CSocket` objekt.

```
CSocket();
```

### <a name="remarks"></a>Poznámky

Po výstavbě je `Create` nutné volat členní funkci.

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketfromhandle"></a><a name="fromhandle"></a>CSocket::FromHandle

Vrátí ukazatel na `CSocket` objekt.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač do soketu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CSocket` objekt nebo NULL, pokud `CSocket` není připojen žádný objekt *hSocket*.

### <a name="remarks"></a>Poznámky

Pokud je k popisovaču `CSocket` přidělen popisovač SOCKET, pokud objekt není připojen k popisovači, členská funkce vrátí hodnotu NULL a nevytvoří dočasný objekt.

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketisblocking"></a><a name="isblocking"></a>csocket::isblocking

Volání této členské funkce k určení, zda probíhá blokování volání.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je zásuvka blokována; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="csocketonmessagepending"></a><a name="onmessagepending"></a>csocket::OnMessagePending CSocket::OnMessagePending CSocket::OnMessagePending CSocket

Přepsat tuto členská funkci hledat konkrétní zprávy ze systému Windows a reagovat na ně v soketu.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

Tohle je pokročilé překažné.

Rozhraní framework `OnMessagePending` volá, zatímco socket je čerpání zpráv systému Windows, aby vám možnost vypořádat se se zprávami, které vás zajímají. Příklady použití naleznete `OnMessagePending`v článku Windows [Sockets: Deriving from Socket Classes](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Další informace naleznete [v tématu Windows Sockets: Using Sockets with Archives](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Viz také

[Třída CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třída CAsyncSocket](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
