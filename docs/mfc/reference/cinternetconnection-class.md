---
title: Třída CInternetConnection
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 6649986f279e010a833b31157922cb4fd1ea8613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372428"
---
# <a name="cinternetconnection-class"></a>Třída CInternetConnection

Spravuje připojení k internetovému serveru.

## <a name="syntax"></a>Syntaxe

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Vytvoří `CInternetConnection` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Získá ID kontextu pro tento objekt připojení.|
|[CInternetConnection::GetServerName](#getservername)|Získá název serveru přidruženého k připojení.|
|[CInternetConnection::GetSession](#getsession)|Získá ukazatel [cInternetSession](../../mfc/reference/cinternetsession-class.md) objekt uspojený s připojením.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetConnection::operátor HINTERNET](#operator_hinternet)|Popisovač relace Internetu.|

## <a name="remarks"></a>Poznámky

Jedná se o základní třídu pro třídy Knihovny MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md)a [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Každá z těchto tříd poskytuje další funkce pro komunikaci s příslušným serverem FTP, HTTP nebo gopher.

Chcete-li komunikovat přímo s internetovým serverem, musíte `CInternetConnection` mít objekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) a objekt.

Další informace o tom, jak fungují třídy WinInet, naleznete v článku [Internetové programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cinternetconnectioncinternetconnection"></a><a name="cinternetconnection"></a>CInternetConnection::CInternetConnection

Tato členská funkce `CInternetConnection` je volána při vytvoření objektu.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pRelace*<br/>
Ukazatel na objekt [CInternetSession.](../../mfc/reference/cinternetsession-class.md)

*server pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*nPort*<br/>
Číslo, které identifikuje internetový port pro toto připojení.

*dwKontext*<br/>
Identifikátor kontextu pro `CInternetConnection` objekt. Další informace o *dwContext*naleznete v **tématu Poznámky** .

### <a name="remarks"></a>Poznámky

Nikdy si `CInternetConnection` neříkáš. místo toho zavolejte člennou funkci [CInternetSession](../../mfc/reference/cinternetsession-class.md) pro typ připojení, který chcete vytvořit:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

Výchozí hodnota pro *dwContext* je odeslána `CInternetConnection`knihovnou MFC do objektu -derived z objektu [CInternetSession,](../../mfc/reference/cinternetsession-class.md) který vytvořil objekt **Object -derived InternetConnection.** Výchozí hodnota je nastavena na hodnotu 1. můžete však explicitně přiřadit konkrétní identifikátor kontextu v konstruktoru [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) pro připojení. Objekt a všechny práce, které provede, budou přidruženy k tomuto ID kontextu. Identifikátor kontextu je [vrácena CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav na objekt, se kterým je identifikován. Další informace o identifikátoru kontextu naleznete v článku [První kroky Internetu: WinInet.](../../mfc/wininet-basics.md)

## <a name="cinternetconnectiongetcontext"></a><a name="getcontext"></a>CInternetConnection::GetContext

Volání této členské funkce získat ID kontextu pro tuto relaci.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Návratová hodnota

ID kontextu přiřazené aplikaci.

### <a name="remarks"></a>Poznámky

ID kontextu je původně zadáno v [CInternetSession](../../mfc/reference/cinternetsession-class.md) a šíří se do `CInternetConnection`- a [CInternetFile](../../mfc/reference/cinternetfile-class.md)-odvozené třídy, pokud není zadáno jinak ve volání funkce, která otevírá připojení. ID kontextu je přidruženo k jakékoli operaci daného objektu a identifikuje informace o stavu operace vrácené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Další informace o `GetContext` tom, jak práce s jinými třídami WinInet poskytnout informace o stavu uživatele, naleznete v článku [Internet First Steps: WinInet](../../mfc/wininet-basics.md) další informace o identifikátor kontextu.

## <a name="cinternetconnectiongetservername"></a><a name="getservername"></a>CInternetConnection::GetServerName

Volánítéto členské funkce získat název serveru přidruženého k tomuto připojení k Internetu.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název serveru, se kterým tento objekt připojení pracuje.

## <a name="cinternetconnectiongetsession"></a><a name="getsession"></a>CInternetConnection::GetSession

Volání této členské funkce získat `CInternetSession` ukazatel na objekt, který je spojen s tímto připojením.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na objekt [CInternetSession](../../mfc/reference/cinternetsession-class.md) přidružený k tomuto objektu připojení k Internetu.

## <a name="cinternetconnectionoperator-hinternet"></a><a name="operator_hinternet"></a>CInternetConnection::operátor HINTERNET

Pomocí tohoto operátoru získáte popisovač na úrovni rozhraní API pro aktuální relaci Internetu.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Viz také

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
