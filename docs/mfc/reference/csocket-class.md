---
title: CSocket – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CSocket [MFC], CSocket
- CSocket [MFC], Attach
- CSocket [MFC], CancelBlockingCall
- CSocket [MFC], Create
- CSocket [MFC], FromHandle
- CSocket [MFC], IsBlocking
- CSocket [MFC], OnMessagePending
ms.assetid: 7f23c081-d24d-42e3-b511-8053ca53d729
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0bfaf418ec78a750f6030683801d00a1450364d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375600"
---
# <a name="csocket-class"></a>CSocket – třída
Odvozená z `CAsyncSocket`, dědí jeho zapouzdření rozhraní Windows Sockets API a představuje vyšší úrovni abstrakce, než `CAsyncSocket` objektu.  
  
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
|[CSocket::Attach](#attach)|Připojí **SOKETU** popisovač `CSocket` objektu.|  
|[CSocket::CancelBlockingCall](#cancelblockingcall)|Zruší blokování volání, které právě probíhá.|  
|[CSocket::Create](#create)|Vytvoří soketu.|  
|[CSocket::FromHandle](#fromhandle)|Vrátí ukazatel na `CSocket` objekt, daný **SOKETU** zpracování.|  
|[CSocket::IsBlocking](#isblocking)|Určuje, zda blokování volání v průběhu.|  
  
### <a name="protected-methods"></a>Chráněné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSocket::OnMessagePending](#onmessagepending)|Voláno k procesu čekajících zpráv při čekání na dokončení blokování volání.|  
  
## <a name="remarks"></a>Poznámky  
 `CSocket` funguje s třídami `CSocketFile` a `CArchive` ke správě odesílání a příjem dat.  
  
 A `CSocket` objekt také poskytuje blokování, které je nezbytné pro synchronní operace `CArchive`. Blokování funkce, jako například `Receive`, `Send`, `ReceiveFrom`, `SendTo`, a `Accept` (všechny zděděné z `CAsyncSocket`), nevrátí `WSAEWOULDBLOCK` došlo k chybě v `CSocket`. Místo toho tyto funkce počkejte na dokončení operace. Kromě toho bude ukončen původní volání s chybou `WSAEINTR` Pokud `CancelBlockingCall` je volána při jednu z těchto funkcí je zablokovaná.  
  
 Použít `CSocket` objektu, volání konstruktoru, pak zavolají `Create` vytvořit základní `SOCKET` zpracování (typ `SOCKET`). Výchozí parametry `Create` vytvořit soket datového proudu, ale pokud nepoužíváte soketu s `CArchive` objekt, můžete zadat parametr, který se vytvořit soket datagram místo, nebo vytvořit vazbu na určitém portu se vytvořit soket serveru. Připojte se k soketu klienta pomocí `Connect` na straně klienta a `Accept` na straně serveru. Pak vytvořte `CSocketFile` objektu a přidružte ji k `CSocket` objekt v `CSocketFile` konstruktor. Dále vytvořte `CArchive` objekt pro odesílání a jeden pro příjem dat (podle potřeby), pak je přidružit `CSocketFile` objekt v `CArchive` konstruktor. Po dokončení komunikace se destroy `CArchive`, `CSocketFile`, a `CSocket` objekty. `SOCKET` Datový typ je popsána v článku [Windows Sockets: pozadí](../../mfc/windows-sockets-background.md).  
  
 Při použití `CArchive` s `CSocketFile` a `CSocket`, může nastat situace, kdy `CSocket::Receive` zadá smyčku (podle `PumpMessages(FD_READ)`) čekání na požadovaný počet bajtů. Důvodem je, že rozhraní Windows sockets povolit pouze jedno volání přijatých za FD_READ oznámení, ale `CSocketFile` a `CSocket` povolit více volání přijatých za FD_READ. Pokud dojde FD_READ po žádná data ke čtení, dojde k zablokování aplikace. Pokud se nikdy jiné FD_READ, aplikace přestane komunikaci přes soketu.  
  
 Tento problém můžete vyřešit následujícím způsobem. V `OnReceive` metoda třídy soketů, volání `CAsyncSocket::IOCtl(FIONREAD, ...)` před voláním `Serialize` metoda třídě zpráv při čtení ze soketu očekávaná data překračuje velikost jednoho paketu protokolu TCP (jednotka MTU střední sítě obvykle alespoň 1096 bajtů). Pokud velikost dostupné dat je menší než je potřeba, počkejte všechna data a přijímat pouze spusťte operace čtení.  
  
 V následujícím příkladu `m_dwExpected` je přibližný počet bajtů, které uživatel očekává. Předpokládá se, že deklarujete ho jinde v kódu.  
  
 [!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocket-class_1.cpp)]  
  
> [!NOTE]
>  Pokud používáte MFC sockets v sekundární vláken v staticky propojené knihovny MFC aplikaci, musí volat `AfxSocketInit` v každé vlákno, která používá sockets k chybě při inicializaci knihovny soketů. Ve výchozím nastavení `AfxSocketInit` je volán jen v primárních vlákno.  
  
 Další informace najdete v tématu [Windows Sockets v prostředí MFC](../../mfc/windows-sockets-in-mfc.md), [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md), [Windows Sockets: jak sokety s archivy pracovní](../../mfc/windows-sockets-how-sockets-with-archives-work.md), [Rozhraní Windows Sockets: posloupnost operací](../../mfc/windows-sockets-sequence-of-operations.md), [rozhraní Windows Sockets: Příklady soketů využívajících archivy](../../mfc/windows-sockets-example-of-sockets-using-archives.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAsyncSocket](../../mfc/reference/casyncsocket-class.md)  
  
 `CSocket`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxsock.h  
  
##  <a name="attach"></a>  CSocket::Attach  
 Volání této funkce člen připojit `hSocket` popisovač `CSocket` objektu.  
  
```  
BOOL Attach(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Obsahuje popisovač pro soket.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěšného funkce.  
  
### <a name="remarks"></a>Poznámky  
 **SOKETU** popisovač je uložený v objektu [m_hSocket](../../mfc/reference/casyncsocket-class.md#m_hsocket) – datový člen.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
### <a name="example"></a>Příklad  
 [!code-cpp[NVC_MFCSocketThread#1](../../mfc/reference/codesnippet/cpp/csocket-class_2.h)]  
  
 [!code-cpp[NVC_MFCSocketThread#2](../../mfc/reference/codesnippet/cpp/csocket-class_3.cpp)]  
  
 [!code-cpp[NVC_MFCSocketThread#3](../../mfc/reference/codesnippet/cpp/csocket-class_4.cpp)]  
  
##  <a name="cancelblockingcall"></a>  CSocket::CancelBlockingCall  
 Volání této funkce člen zrušit blokování volání právě probíhá.  
  
```  
void CancelBlockingCall();
```  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce zruší všechny nevyřízené operace blokování této soketu. Původní blokování volání s chybou přeruší co nejdříve **WSAEINTR**.  
  
 V případě blokování **Connect** operace, implementace rozhraní Windows Sockets se ukončí blokování volání, jakmile to možné, ale nemusí být možné soketu prostředky k uvolnění až po dokončení připojení (a pak bylo nastaveno) nebo vypršení časového limitu. Je to pravděpodobně byly patrné pouze v případě, že aplikace se hned pokusí otevřít nové soket (pokud jsou k dispozici žádné sockets) nebo pro připojení k témuž partnerovi.  
  
 Všechny operace zrušení jiné než **přijmout** soketu můžete nechat v neurčitém stavu. Pokud aplikace zruší blokování operace na soketu, jenom operace, které aplikace může záviset na schopnost provádět na soket je volání **Zavřít**, i když jiné operace může fungovat na některé Windows Sockets implementace. Pokud vyžadujete maximální přenositelnost pro vaši aplikaci, musí být pozor, abyste závisí na provádění operací po Storno.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="create"></a>  CSocket::Create  
 Volání **vytvořit** – členská funkce poté, co vytvořen objekt soketu se vytvořit soket Windows a jeho připojení.  
  
```  
BOOL Create(
    UINT nSocketPort = 0,  
    int nSocketType = SOCK_STREAM,  
    LPCTSTR lpszSocketAddress = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `nSocketPort`  
 Konkrétní port pro použití s soket nebo 0, pokud chcete, aby MFC vyberte port.  
  
 `nSocketType`  
 **SOCK_STREAM** nebo **SOCK_DGRAM**.  
  
 `lpszSocketAddress`  
 Ukazatel na řetězec obsahující síťovou adresu připojené soketu desítkovém číslo, například "128.56.22.8". Předávání **NULL** řetězec pro tento parametr určuje **CSocket** instance má naslouchat činnost klienta na všech síťových rozhraní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, je-li funkce úspěšně; v opačném případě 0 a určitý kód chyby může být načten voláním `GetLastError`.  
  
### <a name="remarks"></a>Poznámky  
 **Vytvoření** pak zavolá **vazby** pro vazbu na zadanou adresu soketu. Jsou podporovány následující typy soketu:  
  
- **SOCK_STREAM** sekvencování, poskytuje spolehlivé, obousměrný, založeného na připojení bajtové datové proudy. Rodina adres Internetu používá protokol TCP (Transmission Control).  
  
- **SOCK_DGRAM** podporuje datagramy, které jsou bez připojení, nespolehlivé vyrovnávací paměti pevné (obvykle malé) maximální délky. Rodina adres Internetu používá protokol UDP (User Datagram). Chcete-li použít tuto možnost, nesmí používat soketu s `CArchive` objektu.  
  
    > [!NOTE]
    >  **Přijmout** – členská funkce trvá odkaz na nový, prázdný `CSocket` objektu jako její parametr. Je nutné vytvořit tento objekt před voláním **přijmout**. Mějte na paměti, že pokud tento objekt soketu prochází oboru, zavře připojení. Nevolejte **vytvořit** pro tento nový objekt soketu.  
  
 Další informace o sokety datového proudu a datagram, najdete v článcích [Windows Sockets: pozadí](../../mfc/windows-sockets-background.md), [Windows Sockets: porty a adresy soketů](../../mfc/windows-sockets-ports-and-socket-addresses.md), a [Windows Sockets: použití Sokety s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="csocket"></a>  CSocket::CSocket  
 Vytvoří `CSocket` objektu.  
  
```  
CSocket();
```  
  
### <a name="remarks"></a>Poznámky  
 Po vytváření, musí volat **vytvořit** – členská funkce.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="fromhandle"></a>  CSocket::FromHandle  
 Vrátí ukazatel na `CSocket` objektu.  
  
```  
static CSocket* PASCAL FromHandle(SOCKET hSocket);
```  
  
### <a name="parameters"></a>Parametry  
 `hSocket`  
 Obsahuje popisovač pro soket.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `CSocket` objekt, nebo **NULL** Pokud neexistuje žádné `CSocket` objekt připojený k `hSocket`.  
  
### <a name="remarks"></a>Poznámky  
 Pokud zadané **SOKETU** zpracování, pokud `CSocket` objektu není připojený k popisovač, vrátí funkce člen **hodnotu NULL** a nevytvoří dočasný objekt.  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="isblocking"></a>  CSocket::IsBlocking  
 Volání této funkce člen lze zjistit blokování volání je v průběhu.  
  
```  
BOOL IsBlocking();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud je blokování soket; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
##  <a name="onmessagepending"></a>  CSocket::OnMessagePending  
 Člen funkci vyhledat konkrétní zprávy ze systému Windows a reagovat na ně v vaší soketu přepište.  
  
```  
virtual BOOL OnMessagePending();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo zpracováno zprávy; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Toto je rozšířené přepisovatelné.  
  
 Volání framework `OnMessagePending` při soketu je čerpání zpráv systému Windows tak, abyste získali příležitost, jak nakládat s zprávy týkající se do vaší aplikace. Příklady, jak je možné použít `OnMessagePending`, najdete v článku [Windows Sockets: odvozování z tříd soketů](../../mfc/windows-sockets-deriving-from-socket-classes.md).  
  
 Další informace najdete v tématu [Windows Sockets: použití soketů s archivy](../../mfc/windows-sockets-using-sockets-with-archives.md).  
  
## <a name="see-also"></a>Viz také  
 [CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CAsyncSocket – třída](../../mfc/reference/casyncsocket-class.md)   
 [CSocketFile – třída](../../mfc/reference/csocketfile-class.md)
