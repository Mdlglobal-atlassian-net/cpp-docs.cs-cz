---
title: Cgopherconnection – třída
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
ms.openlocfilehash: d960d566a63531af211592a7a8ae8f1cb35c5958
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386265"
---
# <a name="cgopherconnection-class"></a>Cgopherconnection – třída

Spravuje připojení k gopher serveru Internet.

> [!NOTE]
>  Třídy `CGopherConnection`, `CGopherFile`, `CGopherFileFind`, `CGopherLocator` a jejich členy jsou zastaralé, protože nebude fungovat na platformě Windows XP, ale budou i nadále fungovat na starší platformy.

## <a name="syntax"></a>Syntaxe

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|Vytvoří `CGopherConnection` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Vytvoří [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu k vyhledání souborů na gopher serveru.|
|[CGopherConnection::GetAttribute](#getattribute)|Načte informace o atributu o gopher objektu.|
|[CGopherConnection::OpenFile](#openfile)|Otevře soubor gopher.|

## <a name="remarks"></a>Poznámky

Služba gopher je jedním z tři služby Internet rozpoznat pomocí tříd WinInet knihovny MFC.

Třída `CGopherConnection` obsahuje konstruktor a tři další členské funkce, které spravují gopher služby: [OpenFile](#openfile), [CreateLocator](#createlocator), a [GetAttribute](#getattribute).

Ke komunikaci s gopher serveru Internet, musíte nejprve vytvořit instanci [cinternetsession –](../../mfc/reference/cinternetsession-class.md)a pak vyvolejte [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), která vytvoří `CGopherConnection` objekt a vrátí ukazatel na něj. Nikdy nevytvářejte `CGopherConnection` objektu přímo.

Další informace o tom, `CGopherConnection` funguje s jinými třídami MFC Internetu najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md). Další informace o použití další dvě podporované služby sítě Internet, HTTP a FTP zobrazit třídy [chttpconnection –](../../mfc/reference/chttpconnection-class.md) a [cftpconnection –](../../mfc/reference/cftpconnection-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

Tato členská funkce je volána k sestavení kompletních `CGopherConnection` objektu.

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

*pSession*<br/>
Ukazatel na související [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu.

*hConnected*<br/>
Popisovač Windows aktuální relace Internet.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru FTP.

*dwContext*<br/>
Identifikátor kontextu operace. *dwContext* identifikuje informace o stavu operace vracené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback). Výchozí hodnota je nastavená na 1; Můžete však explicitně přiřadit konkrétní kontext ID operace. Objekt a veškerou práci, kterou provádí bude spojená s ID tohoto kontextu.

*pstrUserName*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje jméno uživatele k přihlášení. Pokud má hodnotu NULL, výchozí hodnota je anonymous.

*pstrPassword*<br/>
Ukazatel na řetězec zakončený hodnotou null, který určuje heslo pro použití k protokolování. Pokud mají oba *pstrPassword* a *pstrUserName* hodnotu Null, je výchozí heslo anonymní uživatelské jméno e-mailu. Pokud *pstrPassword* má hodnotu NULL (nebo prázdný řetězec), ale *pstrUserName* nemá hodnotu NULL, prázdné heslo se používá. Následující tabulka popisuje chování pro čtyři možných nastavení *pstrUserName* a *pstrPassword*:

|*pstrUserName*|*pstrPassword*|Uživatelské jméno odeslané na FTP server|Heslo odeslaných na FTP server|
|--------------------|--------------------|---------------------------------|---------------------------------|
|Hodnotu NULL nebo ""|Hodnotu NULL nebo ""|"anonymní"|Uživatelské jméno e-mailu|
|Řetězec NENULOVÉ|Hodnotu NULL nebo ""|*pstrUserName*|" "|
|Řetězec s NENULOVOU hodnotou NULL|CHYBA|CHYBA||
|Řetězec NENULOVÉ|Řetězec NENULOVÉ|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
Číslo, které identifikuje port TCP/IP pro použití na serveru.

### <a name="remarks"></a>Poznámky

Nikdy nevytvářejte `CGopherConnection` přímo. Místo toho volat [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection), která vytvoří `CGopherConnection` objekt a vrátí ukazatel na něj.

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

Voláním této členské funkce, pokud chcete vytvořit lokátor gopher najít nebo identifikovat souborů na gopher serveru.

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

*pstrDisplayString*<br/>
Ukazatel na řetězec obsahující název dokumentu gopher nebo adresář, který se má načíst. Pokud *pstrDisplayString* parametr hodnotu NULL, je vrácena výchozí adresář pro gopher serveru.

*pstrSelectorString*<br/>
Ukazatel na řetězec selektor k odeslání na gopher serveru za účelem načtení položky. *pstrSelectorString* může mít hodnotu NULL.

*dwGopherType*<br/>
Toto nastavení určuje, zda *pstrSelectorString* odkazuje na adresář nebo dokument, a zda je požadavek gopher nebo gopher +. Zobrazte atributy, které pro strukturu [GOPHER_FIND_DATA](/windows/desktop/api/wininet/ns-wininet-gopher_find_dataa) v sadě Windows SDK.

*pstrLocator*<br/>
Ukazatel na řetězec, který identifikuje soubor otevřete. Obecně platí, tento řetězec je vrácen z volání [CGopherFileFind::GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator).

*pstrServerName*<br/>
Ukazatel na řetězec obsahující název gopher serveru.

*nPort*<br/>
Číslo identifikující Internet port pro toto připojení.

### <a name="return-value"></a>Návratová hodnota

A [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.

### <a name="remarks"></a>Poznámky

Verze statické členské funkce vyžaduje, abyste k určení serveru, zatímco verze nestatické používá název serveru z objekt připojení.

K načtení informací ze serveru gopher, musíte aplikace nejdřív získat gopher lokátoru. Aplikace musí pak považovat za Lokátor neprůhledné token (to znamená, aplikace můžete použít Lokátor, ale ne přímo manipulaci s nebo porovnání). Za normálních okolností aplikace používá Lokátor pro volání [CGopherFileFind::FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) členská funkce vyhledat konkrétní informace.

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

Zavolejte tuto členskou funkci ze serveru gopher načíst konkrétní atribut informace o položce.

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.

*strRequestedAttributes*<br/>
Mezerami oddělený řetězec určující názvy požadovaných atributů.

*strResult*<br/>
Odkaz na [CString](../../atl-mfc-shared/reference/cstringt-class.md) , která přijímá Typ lokátoru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0. Pokud volání selže, funkci Win32 [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360) může být volána a zjistěte příčinu chyby.

##  <a name="openfile"></a>  CGopherConnection::OpenFile

Voláním této členské funkce pro otevření souboru na gopher serveru.

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*refLocator*<br/>
Odkaz na [cgopherlocator –](../../mfc/reference/cgopherlocator-class.md) objektu.

*dwFlags*<br/>
Jakékoli kombinace příznaků INTERNET_FLAG_ *. Zobrazit [CInternetSession::OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) Další informace o INTERNET_FLAG_\* příznaky.

*pstrView*<br/>
Ukazatel na řetězec zobrazení souboru. Pokud několik zobrazení souboru na serveru, tento parametr určuje, které soubor zobrazení se otevře. Pokud *pstrView* má hodnotu NULL, výchozího zobrazení souboru se používá.

*dwContext*<br/>
ID kontextu pro soubor je otevřený. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cgopherfile –](../../mfc/reference/cgopherfile-class.md) objektu, který chcete otevřít.

### <a name="remarks"></a>Poznámky

Přepsat *dwContext* výchozí identifikátor kontextu nastavena na hodnotu podle vašeho výběru. Identifikátor kontextu souvisí s tuto konkrétní operaci `CGopherConnection` objekt vytvořený pomocí jeho [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu. Hodnota se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) kvůli stavu na operaci, se kterým je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

## <a name="see-also"></a>Viz také:

[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection – třída](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection – třída](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection – třída](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator – třída](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile – třída](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession – třída](../../mfc/reference/cinternetsession-class.md)
