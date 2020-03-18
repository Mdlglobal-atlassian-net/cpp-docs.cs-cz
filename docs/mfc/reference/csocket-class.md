---
title: CSocket – – třída
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
ms.openlocfilehash: a861e557b7368d13d615aaf796faded93c72b040
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421168"
---
# <a name="csocket-class"></a>CSocket – – třída

Je odvozen z `CAsyncSocket`dědí jeho zapouzdření rozhraní Windows Sockets API a představuje vyšší úroveň abstrakce než objekt `CAsyncSocket`.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSocket –:: CSocket –](#csocket)|Vytvoří objekt `CSocket`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSocket –:: Attach](#attach)|Připojí popisovač SOKETu k objektu `CSocket`.|
|[CSocket –:: CancelBlockingCall](#cancelblockingcall)|Zruší blokující volání, které aktuálně probíhá.|
|[CSocket –:: Create](#create)|Vytvoří soket.|
|[CSocket –:: FromHandle](#fromhandle)|Vrátí ukazatel na objekt `CSocket`, který má přidělený popisovač SOKETu.|
|[CSocket –::-Blocking](#isblocking)|Určuje, zda probíhá blokující volání.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CSocket –:: OnMessagePending](#onmessagepending)|Volá se, aby se zpracovaly čekající zprávy při čekání na dokončení blokujícího volání.|

## <a name="remarks"></a>Poznámky

`CSocket` pracuje s třídami `CSocketFile` a `CArchive` ke správě odesílání a přijímání dat.

Objekt `CSocket` také poskytuje blokování, které je nezbytné pro synchronní operaci `CArchive`. Blokování funkcí, například `Receive`, `Send`, `ReceiveFrom`, `SendTo`a `Accept` (vše zděděných z `CAsyncSocket`), nevrátí `WSAEWOULDBLOCK` chybu `CSocket`. Místo toho tyto funkce čekají na dokončení operace. Kromě toho původní volání skončí s chybou WSAEINTR, pokud je volána `CancelBlockingCall`, zatímco jedna z těchto funkcí je blokována.

Chcete-li použít objekt `CSocket`, zavolejte konstruktor a pak voláním `Create` vytvořte základní popisovač SOKETu (typ SOKETu). Výchozí parametry `Create` vytvořit soket streamu, ale pokud nepoužíváte soket s objektem `CArchive`, můžete místo toho zadat parametr pro vytvoření soketu datagramu nebo vytvoření vazby na konkrétní port pro vytvoření soketu serveru. Připojte se ke klientskému soketu pomocí `Connect` na straně klienta a `Accept` na straně serveru. Pak vytvořte objekt `CSocketFile` a přidružte jej k objektu `CSocket` v konstruktoru `CSocketFile`. Dále vytvořte objekt `CArchive` pro odeslání a jeden pro příjem dat (podle potřeby) a pak je přidružte k objektu `CSocketFile` v konstruktoru `CArchive`. Po dokončení komunikace zničí objekty `CArchive`, `CSocketFile`a `CSocket`. Datový typ SOKETu je popsaný v článku [Windows Sockets: pozadí](../../mfc/windows-sockets-background.md).

Pokud používáte `CArchive` s `CSocketFile` a `CSocket`, může dojít k situaci, kdy `CSocket::Receive` vstoupí do smyčky (`PumpMessages(FD_READ)`) čekající na vyžádané množství bajtů. Důvodem je to, že sokety systému Windows umožňují pouze jedno přijmout volání na oznámení FD_READ, ale `CSocketFile` a `CSocket` umožňují více přijmout volání na FD_READ. Pokud se zobrazí FD_READ, když nejsou k dispozici žádná data ke čtení, aplikace přestane reagovat. Pokud nikdy nezískáte další FD_READ, aplikace přestane komunikovat přes soket.

Tento problém můžete vyřešit následujícím způsobem. V metodě `OnReceive` třídy soketu volejte `CAsyncSocket::IOCtl(FIONREAD, ...)` před voláním metody `Serialize` vaší třídy zpráv, když očekávaná data, která mají být načtena ze soketu, překročí velikost jednoho paketu TCP (maximální přenosová jednotka síťového média, obvykle alespoň 1096 bajtů). Pokud je velikost dostupných dat menší, než je potřeba, počkejte na přijetí všech dat a pak spusťte operaci čtení.

V následujícím příkladu je `m_dwExpected` přibližný počet bajtů, které uživatel očekává k přijetí. Předpokládá se, že deklarujete ho jinde ve svém kódu.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Při použití soketů MFC v sekundárních vláknech v staticky propojené aplikaci MFC je nutné volat `AfxSocketInit` v každém vlákně, které používá sokety k inicializaci knihoven soketu. Ve výchozím nastavení je `AfxSocketInit` volána pouze v primárním vlákně.

Další informace najdete v tématu rozhraní [Windows Sockets v prostředí MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md), rozhraní [Windows Sockets: jak pracují sokety s archivy](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Windows Sockets: posloupnost operací](../../mfc/windows-sockets-sequence-of-operations.md), [Windows Sockets: příklad soketů pomocí archivů](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Požadavky

**Záhlaví:** AfxSock. h

##  <a name="attach"></a>CSocket –:: Attach

Zavolejte tuto členskou funkci pro připojení `hSocket`ho popisovače k objektu `CSocket`.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač pro soket.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Popisovač SOKETu je uložený v datovém členu [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) objektu.

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>CSocket –:: CancelBlockingCall

Zavolejte tuto členskou funkci pro zrušení aktuálně probíhajícího blokujícího volání.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Poznámky

Tato funkce zruší všechny zbývající operace blokování pro tento soket. Původní blokující volání bude co nejdříve ukončeno s chybou WSAEINTR.

V případě blokujícího `Connect` operace rozhraní Windows Sockets ukončí blokující volání co nejrychleji, ale nemusí být možné, aby se uvolnily prostředky soketu, dokud se připojení nedokončí (a pak bylo resetované) nebo vypršel časový limit. To je pravděpodobně patrné pouze v případě, že se aplikace pokusí otevřít nový soket (pokud nejsou k dispozici žádné sokety) nebo se má připojit ke stejnému partnerovi.

Zrušení jakékoli jiné operace, než je `Accept`, může způsobit, že soket nebude v neurčitém stavu. Pokud aplikace zruší blokující operaci na soketu, jedinou operací, kterou může aplikace provést na soketu, je volání `Close`, i když jiné operace mohou fungovat i u některých implementací rozhraní Windows Sockets. Pokud si přejete maximální přenositelnost vaší aplikace, musíte mít pozor, abyste po zrušení nemuseli záviset na provádění operací.

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>CSocket –:: Create

Po vytvoření objektu soketu pro vytvoření soketu Windows a jeho připojení zavolejte funkci **Create** member.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Konkrétní port, který má být použit s soketem, nebo 0, pokud chcete vybrat port v knihovně MFC.

*nSocketType*<br/>
SOCK_STREAM nebo SOCK_DGRAM.

*lpszSocketAddress*<br/>
Ukazatel na řetězec, který obsahuje síťovou adresu připojeného soketu, číslo s tečkami, například "128.56.22.8". Předání řetězce s hodnotou NULL pro tento parametr znamená, že instance `CSocket` by měla naslouchat aktivitě klienta na všech síťových rozhraních.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; jinak 0 a konkrétní kód chyby lze načíst voláním `GetLastError`.

### <a name="remarks"></a>Poznámky

`Create` pak zavolá `Bind`, aby se soket navázal na zadanou adresu. Podporovány jsou následující typy soketů:

- SOCK_STREAM poskytuje sekvenční, spolehlivé a obousměrné datové proudy založené na připojení. Používá protokol TCP (Transmission Control Protocol) pro rodinu internetových adres.

- SOCK_DGRAM podporuje datagramy, které jsou bez připojení, nespolehlivé vyrovnávací paměti pevné (obvykle malé) maximální délka. Používá pro rodinu internetových adres protokol UDP (User Datagram Protocol). Chcete-li použít tuto možnost, nesmí být soket použit s objektem `CArchive`.

    > [!NOTE]
    >  Členská funkce `Accept` přebírá odkaz na nový prázdný objekt `CSocket` jako svůj parametr. Tento objekt je nutné vytvořit před voláním `Accept`. Mějte na paměti, že pokud se tento objekt soketu dostane mimo rozsah, připojení se zavře. Nevolejte `Create` pro tento nový objekt soketu.

Další informace o streamování a soketech datagram najdete v článcích [Windows Sockets: Background](../../mfc/windows-sockets-background.md), [Windows Sockets: ports and Sockets](../../mfc/windows-sockets-ports-and-socket-addresses.md)a [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>CSocket –:: CSocket –

Vytvoří objekt `CSocket`.

```
CSocket();
```

### <a name="remarks"></a>Poznámky

Po konstrukci je nutné zavolat členskou funkci `Create`.

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>CSocket –:: FromHandle

Vrátí ukazatel na objekt `CSocket`.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač pro soket.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt `CSocket` nebo hodnotu NULL, pokud není k *hSocket*připojen žádný objekt `CSocket`.

### <a name="remarks"></a>Poznámky

Pokud je předána obslužná rutina SOKETu, pokud objekt `CSocket` není připojen k popisovači, vrátí členská funkce hodnotu NULL a nevytvoří dočasný objekt.

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>CSocket –::-Blocking

Zavolejte tuto členskou funkci, abyste zjistili, jestli probíhá blokující volání.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je blokována zásuvka; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>CSocket –:: OnMessagePending

Tuto členskou funkci přepište, pokud chcete vyhledat konkrétní zprávy ze systému Windows a reagovat na ně ve vašem soketu.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zpráva zpracována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Toto je pokročilá přepsatelné.

Rozhraní volá `OnMessagePending`, zatímco soket vyřadí zprávy systému Windows, a poskytne vám možnost zabývat se zprávami, které vás zajímají. Příklady použití `OnMessagePending`naleznete v článku rozhraní [Windows Sockets: odvozování z tříd soketů](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Viz také

[CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
