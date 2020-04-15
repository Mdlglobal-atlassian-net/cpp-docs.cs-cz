---
title: Třída CGopherConnection
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: eade1a82b674d5ad2e91146559139445ef017180
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373703"
---
# <a name="cgopherconnection-class"></a>Třída CGopherConnection

Spravuje připojení k internetovému serveru gopher.

> [!NOTE]
> Třídy `CGopherConnection` `CGopherFile`, `CGopherFileFind` `CGopherLocator` , a jejich členové byly zastaralé, protože nefungují na platformě systému Windows XP, ale budou pokračovat v práci na dřívějších platformách.

## <a name="syntax"></a>Syntaxe

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Vytvoří `CGopherConnection` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Vytvoří objekt [CGopherLocator](../../mfc/reference/cgopherlocator-class.md) pro vyhledání souborů na serveru gopher.|
|[CGopherConnection::Atribut GetAttribute](#getattribute)|Načte informace o atributu objektu gopher.|
|[CGopherConnection::OpenFile](#openfile)|Otevře soubor gopher.|

## <a name="remarks"></a>Poznámky

Služba gopher je jednou ze tří internetových služeb uznávaných třídami MFC WinInet.

Třída `CGopherConnection` obsahuje konstruktor a tři další členské funkce, které spravují gopher služby: [OpenFile](#openfile), [CreateLocator](#createlocator)a [GetAttribute](#getattribute).

Chcete-li komunikovat s internetovým serverem gopher, musíte nejprve vytvořit instanci [CInternetSession](../../mfc/reference/cinternetsession-class.md)a potom `CGopherConnection` zavolat [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), který vytvoří objekt a vrátí mu ukazatel. Nikdy nevytváříte `CGopherConnection` objekt přímo.

Další informace o `CGopherConnection` práci s ostatními třídami MFC Internet naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o použití dalších dvou podporovaných internetových služeb FTP a HTTP naleznete v třídách [CHttpConnection](../../mfc/reference/chttpconnection-class.md) a [CFtpConnection](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cgopherconnectioncgopherconnection"></a><a name="cgopherconnection"></a>CGopherConnection::CGopherConnection

Tato členská funkce je `CGopherConnection` volána k vytvoření objektu.

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*pRelace*<br/>
Ukazatel na související objekt [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*hPřipojeno*<br/>
Popisovač systému Windows aktuální relace Internetu.

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*dwKontext*<br/>
Identifikátor kontextu pro operaci. *dwContext* identifikuje informace o stavu operace vrácené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Výchozí hodnota je nastavena na hodnotu 1. můžete však explicitně přiřadit konkrétní ID kontextu pro operaci. Objekt a všechny práce, které provede, budou přidruženy k tomuto ID kontextu.

*pstrUserName*<br/>
Ukazatel na řetězec s ukončeným hodnotou null, který určuje jméno uživatele, který se má přihlásit. Pokud null, výchozí hodnota je anonymní.

*pstrPassword*<br/>
Ukazatel na řetězec s nulovým ukončením, který určuje heslo, které se má použít k přihlášení. Pokud jsou *hodnota pstrPassword* i *pstrUserName* null, je výchozím anonymním heslem e-mailové jméno uživatele. Pokud *pstrPassword* je NULL (nebo prázdný řetězec), ale *pstrUserName* není NULL, je použito prázdné heslo. Následující tabulka popisuje chování pro čtyři možná nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané serveru FTP|Heslo odeslané na server FTP|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Null nebo " "|Null nebo " "|"anonymní"|E-mailová značka uživatele|
|Ne- nulový řetězec|Null nebo " "|*pstrUserName*|" "|
|Null non- NULL řetězec|ERROR|ERROR||
|Ne- nulový řetězec|Ne- nulový řetězec|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo, které identifikuje port TCP/IP, který má být na serveru používán.

### <a name="remarks"></a>Poznámky

Nikdy nevytváříte `CGopherConnection` přímo. Místo toho volání [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection) `CGopherConnection` , který vytvoří objekt a vrátí ukazatel na něj.

## <a name="cgopherconnectioncreatelocator"></a><a name="createlocator"></a>CGopherConnection::CreateLocator

Volání této členské funkce k vytvoření gopher lokátor najít nebo identifikovat soubor na gopher serveru.

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>Parametry

*strstrDisplayString*<br/>
Ukazatel na řetězec obsahující název gopher dokumentu nebo adresáře, který má být načten. Pokud je parametr *pstrDisplayString* null, je vrácen výchozí adresář serveru gopher.

*řetězec pstrSelectorString*<br/>
Ukazatel na řetězec voliče, který má být odeslán na server gopher za účelem načtení položky. *pstrSelectorString* může být NULL.

*dwGopherTyp*<br/>
Určuje, zda *pstrSelectorString* odkazuje na adresář nebo dokument a zda je požadavek gopher nebo gopher+. Podívejte se na atributy struktury [GOPHER_FIND_DATA](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw) v sadě Windows SDK.

*pstrLocator*<br/>
Ukazatel na řetězec identifikující soubor, který má být otevřen. Obecně platí, že tento řetězec je vrácena z volání [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*název serveru pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru gopher.

*nPort*<br/>
Číslo identifikující internetový port pro toto připojení.

### <a name="return-value"></a>Návratová hodnota

[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) objektu.

### <a name="remarks"></a>Poznámky

Statická verze členské funkce vyžaduje zadání serveru, zatímco nestatická verze používá název serveru z objektu připojení.

Chcete-li načíst informace ze serveru gopher, aplikace musí nejprve získat gopher lokátor. Aplikace pak musí považovat lokátor za neprůhledný token (to znamená, že aplikace může použít lokátor, ale není přímo manipulovat nebo jej porovnat). Za normálních okolností aplikace používá lokátor pro volání [cgopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) členské funkce načíst konkrétní část informace.

## <a name="cgopherconnectiongetattribute"></a><a name="getattribute"></a>CGopherConnection::Atribut GetAttribute

Volání této členské funkce k načtení konkrétních informací o atributu o položce ze serveru gopher.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na objekt [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*strRequestedAtributy*<br/>
Řetězec oddělený mezerami určující názvy požadovaných atributů.

*strVýsledek*<br/>
Odkaz na [CString,](../../atl-mfc-shared/reference/cstringt-class.md) který přijímá typ lokátoru.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0. Pokud se volání nezdaří, win32 funkce [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) může být volána k určení příčiny chyby.

## <a name="cgopherconnectionopenfile"></a><a name="openfile"></a>CGopherConnection::OpenFile

Volánítéto členské funkce otevřete soubor na serveru gopher.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na objekt [CGopherLocator.](../../mfc/reference/cgopherlocator-class.md)

*dwFlags*<br/>
Libovolná kombinace INTERNET_FLAG_* příznaků. Další informace o INTERNET_FLAG_\* příznaků naleznete v tématu [CInternetSession::OpenUrl.](../../mfc/reference/cinternetsession-class.md#openurl)

*zobrazení pstrView*<br/>
Ukazatel na řetězec zobrazení souboru. Pokud na serveru existuje několik zobrazení souboru, tento parametr určuje, které zobrazení souboru se má otevřít. Pokud *je hodnota pstrView* null, použije se výchozí zobrazení souboru.

*dwKontext*<br/>
ID kontextu pro soubor, který se otevírá. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="return-value"></a>Návratová hodnota

Ukazatel na [cgopherfile](../../mfc/reference/cgopherfile-class.md) objektu, který má být otevřen.

### <a name="remarks"></a>Poznámky

Přepište *výchozí hodnotu dwContext* a nastavte identifikátor kontextu na hodnotu podle vašeho výběru. Identifikátor kontextu je spojen s touto `CGopherConnection` konkrétní operací objektu vytvořeného jeho objektem [CInternetSession.](../../mfc/reference/cinternetsession-class.md) Hodnota je vrácena [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav operace, s níž je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="see-also"></a>Viz také

[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[Třída Připojení Chttp](../../mfc/reference/chttpconnection-class.md)<br/>
[Třída CInternetConnection](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
