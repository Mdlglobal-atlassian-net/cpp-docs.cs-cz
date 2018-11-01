---
title: Csocket – třída
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
ms.openlocfilehash: 3c5340a8c65f804747fd8d3c8bd31fb20f80c6ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487276"
---
# <a name="csocket-class"></a>Csocket – třída

Je odvozen od `CAsyncSocket`dědí její zapouzdření Windows Sockets API a představuje vyšší úroveň abstrakce, než `CAsyncSocket` objektu.

## <a name="syntax"></a>Syntaxe

```
class CSocket : public CAsyncSocket
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSocket::CSocket](#csocket)|Vytvoří `CSocket` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CSocket::Attach](#attach)|Připojí popisovač SOKETU `CSocket` objektu.|
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Zruší blokovacího hovoru, který právě probíhá.|
|[CSocket::Create](#create)|Vytvoří soket.|
|[CSocket::FromHandle](#fromhandle)|Vrací ukazatel `CSocket` objekt daný popisovač SOKETU.|
|[CSocket::IsBlocking](#isblocking)|Určuje, zda blokovacího hovoru probíhá.|

### <a name="protected-methods"></a>Chráněné metody

|Název|Popis|
|----------|-----------------|
|[CSocket::OnMessagePending](#onmessagepending)|Volá se, aby proces čekajících zpráv při čekání na dokončení blokování volání.|

## <a name="remarks"></a>Poznámky

`CSocket` funguje s třídami `CSocketFile` a `CArchive` ke správě odesílání a příjem data.

A `CSocket` objekt také poskytuje k blokování, což je nezbytné pro synchronní operace `CArchive`. Blokuje funkce, jako například `Receive`, `Send`, `ReceiveFrom`, `SendTo`, a `Accept` (všechny zděděné z `CAsyncSocket`), nevrátí `WSAEWOULDBLOCK` při `CSocket`. Tyto funkce místo toho Počkejte, dokud se operace dokončí. Kromě toho původní volání Pokud dojde k ukončení s chybou WSAEINTR `CancelBlockingCall` je volána, když některou z těchto funkcí je blokování.

Použití `CSocket` objektu, volání konstruktoru, zavolejte `Create` vytvořit základní popisovač SOKETU (typ SOKETU). Výchozí parametry `Create` vytvořit soket datového proudu, ale v případě, že nepoužíváte soketu se `CArchive` objektu, můžete zadat parametr, který se místo toho vytvořit soket datagram nebo vytvořit vazbu na určitém portu pro vytvoření serverového soketu. Připojení k soketu klienta pomocí `Connect` na straně klienta a `Accept` na straně serveru. Pak vytvořte `CSocketFile` objektu a přidružte ho k `CSocket` objekt `CSocketFile` konstruktor. Dále vytvořte `CArchive` objektu pro odesílání a jeden pro příjem dat (podle potřeby), potom je přidružte `CSocketFile` objekt `CArchive` konstruktoru. Po dokončení komunikace se zničit `CArchive`, `CSocketFile`, a `CSocket` objekty. Datový typ SOCKET je popsaný v článku [rozhraní Windows Sockets: pozadí](../../mfc/windows-sockets-background.md).

Při použití `CArchive` s `CSocketFile` a `CSocket`, může nastat situace, kdy `CSocket::Receive` přejde do smyčky (podle `PumpMessages(FD_READ)`) čekající na požadovaný počet bajtů. Důvodem je, že rozhraní Windows sockets povolit pouze jedno volání přijatých za FD_READ oznámení, ale `CSocketFile` a `CSocket` povolit více volání přijatých za FD_READ. Pokud dojde FD_READ když nejsou žádná data ke čtení, dojde k zablokování aplikace. Pokud obdržíte nikdy jiného FD_READ, že aplikace přestane komunikaci přes soket.

Tento problém lze vyřešit následovně. V `OnReceive` metoda třídy soketů, volání `CAsyncSocket::IOCtl(FIONREAD, ...)` před voláním `Serialize` metody třídy zpráv při očekávaná data ke čtení ze soketu překračuje velikost jednoho TCP paketu (MTU jednotky média sítě obvykle alespoň 1096 bajtů). Pokud velikost dostupných dat je menší než je potřeba, počkejte všechna data na přijmout a teprve potom začne operace čtení.

V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává. Předpokládá se, že se deklaruje jinde ve vašem kódu.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]

> [!NOTE]
>  Při použití soketů knihovny MFC v sekundárních vláken aplikace staticky propojené knihovny MFC, je nutné volat `AfxSocketInit` v každém vlákně, který používá sockets k inicializaci soketu knihovny. Ve výchozím nastavení `AfxSocketInit` je volána pouze v primárním vlákně.

Další informace najdete v tématu [Windows Sockets v prostředí MFC](../../mfc/windows-sockets-in-mfc.md), [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md), [rozhraní Windows Sockets: jak sokety s archivy pracovní](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Rozhraní Windows Sockets: posloupnost operací](../../mfc/windows-sockets-sequence-of-operations.md), [rozhraní Windows Sockets: Příklady soketů využívajících archivy](../../mfc/windows-sockets-example-of-sockets-using-archives.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CAsyncSocket](../../mfc/reference/casyncsocket-class.md)

`CSocket`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxsock.h

##  <a name="attach"></a>  CSocket::Attach

Voláním této členské funkce se připojit `hSocket` popisovače `CSocket` objektu.

```
BOOL Attach(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač soketu.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná.

### <a name="remarks"></a>Poznámky

Popisovač SOKETU je uložena v objektu [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) datový člen.

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]

[!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]

[!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]

##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall

Voláním této členské funkce zrušit blokování volání právě probíhá.

```
void CancelBlockingCall();
```

### <a name="remarks"></a>Poznámky

Tato funkce zruší všechny zbývající blokující operace pro tento soket. Původní blokovacího hovoru se co nejdříve ukončit s chybou WSAEINTR.

V případě blokování `Connect` operace, implementace rozhraní Windows Sockets se ukončí blokovacího hovoru, poté, co možná, ale nemusí být možné soketu prostředky, které mají být uvolněna až do připojení dokončil (a poté byla obnovena) nebo Vypršel časový limit. To je pravděpodobně být patrné pouze v případě, že aplikace okamžitě se pokusí otevřít soket nová (pokud jsou k dispozici žádné sockets), nebo pro připojení k témuž.

Všechny operace rušení jiné než `Accept` soketu ponechán v neurčitém stavu. Pokud aplikace zruší blokující operace se soketem, jedinou operací, která aplikace může záviset na schopnost provádět na soket je volání `Close`, i když jiné operace může fungovat v některých implementacích rozhraní Windows Sockets. Pokud vyžadujete maximální přenositelnost pro vaše aplikace, musí být pozor, abyste závisí na provádění operací po zrušení.

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="create"></a>  CSocket::Create

Volání **vytvořit** členskou funkci po vytváření objekt soketu soketu Windows vytvořit a připojit ji.

```
BOOL Create(
    UINT nSocketPort = 0,
    int nSocketType = SOCK_STREAM,
    LPCTSTR lpszSocketAddress = NULL);
```

### <a name="parameters"></a>Parametry

*nSocketPort*<br/>
Konkrétní port pro použití s soketu, nebo 0, pokud chcete, aby knihovny MFC pro výběr portu.

*nSocketType*<br/>
SOCK_STREAM nebo SOCK_DGRAM.

*lpszSocketAddress*<br/>
Ukazatel na řetězec obsahující síťová adresa připojený soket tečkovaná číslo, například "128.56.22.8". Předání NULL řetězec pro tento parametr určuje `CSocket` instance naslouchat požadavkům klientů na všech síťových rozhraních.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je funkce úspěšná; v opačném případě 0 a určitý kód chyby může být načten voláním `GetLastError`.

### <a name="remarks"></a>Poznámky

`Create` pak zavolá `Bind` soketu vytvořit vazbu na zadané adrese. Jsou podporovány následující typy soketu:

- SOCK_STREAM poskytuje sekvencování, spolehlivé obousměrné, na základě připojení bajtové datové proudy. Používá protokol TCP (Transmission Control) pro rodinu adres sítě Internet.

- Datagramy SOCK_DGRAM podporuje, které jsou nespolehlivé, bez vyrovnávací paměti pevné (obvykle malý) maximální délky. Používá protokol UDP (User Datagram) pro rodinu adres sítě Internet. Pokud chcete použít tuto možnost, nesmí používat soketu se `CArchive` objektu.

    > [!NOTE]
    >  `Accept` Členská funkce používá odkaz na nový, prázdný `CSocket` objektu jako svůj parametr. Je nutné vytvořit tento objekt před voláním `Accept`. Mějte na paměti, která pokud je tento objekt soketu se odesílá z oboru, ukončí připojení. Nevolejte `Create` pro tento nový objekt soketu.

Další informace o streamu a datagram sokety, najdete v článcích [rozhraní Windows Sockets: pozadí](../../mfc/windows-sockets-background.md), [rozhraní Windows Sockets: porty a adresy soketů](../../mfc/windows-sockets-ports-and-socket-addresses.md), a [rozhraní Windows Sockets: použití Sokety s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="csocket"></a>  CSocket::CSocket

Vytvoří `CSocket` objektu.

```
CSocket();
```

### <a name="remarks"></a>Poznámky

Po vytvoření, je třeba zavolat `Create` členskou funkci.

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="fromhandle"></a>  CSocket::FromHandle

Vrací ukazatel `CSocket` objektu.

```
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```

### <a name="parameters"></a>Parametry

*hSocket*<br/>
Obsahuje popisovač soketu.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na `CSocket` objektu, nebo hodnota NULL, pokud neexistuje žádný `CSocket` objekt připojen k *hSocket*.

### <a name="remarks"></a>Poznámky

Když je zadaný popisovač SOKETU, pokud `CSocket` objekt není připojen ke popisovač, členská funkce vrátí hodnotu NULL a nelze vytvořit dočasný objekt.

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="isblocking"></a>  CSocket::IsBlocking

Voláním této členské funkce k určení, zda je blokovacího hovoru probíhá.

```
BOOL IsBlocking();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je blokování soketu; jinak 0.

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

##  <a name="onmessagepending"></a>  CSocket::OnMessagePending

Přepište tato členská funkce vyhledat konkrétní zprávy z Windows a reagovat na ně ve vaší soketu.

```
virtual BOOL OnMessagePending();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva byla zpracována; jinak 0.

### <a name="remarks"></a>Poznámky

To je moderní overridable.

Rámec volá `OnMessagePending` při soketu je – čerpání zpráv Windows vám poskytnou příležitost se zprávy, abyste vaší aplikace. Příklady použití `OnMessagePending`, najdete v článku [rozhraní Windows Sockets: odvozování z tříd soketů](../../mfc/windows-sockets-deriving-from-socket-classes.md).

Další informace najdete v tématu [rozhraní Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).

## <a name="see-also"></a>Viz také

[CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
