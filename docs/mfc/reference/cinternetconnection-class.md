---
title: Cinternetconnection – třída
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
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275347"
---
# <a name="cinternetconnection-class"></a>Cinternetconnection – třída

Spravuje připojení k internetovému serveru.

## <a name="syntax"></a>Syntaxe

```
class CInternetConnection : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|Vytvoří `CInternetConnection` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|Získá ID kontextu pro tento objekt připojení.|
|[CInternetConnection::GetServerName](#getservername)|Získá název serveru přidružené k připojení.|
|[CInternetConnection::GetSession](#getsession)|Získá ukazatel [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt přidružený k připojení.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Popisovač pro relaci Internet.|

## <a name="remarks"></a>Poznámky

Je základní třída pro třídy MFC [cftpconnection –](../../mfc/reference/cftpconnection-class.md), [chttpconnection –](../../mfc/reference/chttpconnection-class.md), a [cgopherconnection –](../../mfc/reference/cgopherconnection-class.md). Každá z těchto tříd poskytuje další funkce pro komunikaci se na příslušný server FTP, HTTP nebo gopher.

Pro přímou komunikaci se serverem v Internetu, musíte mít [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu a `CInternetConnection` objektu.

Další informace o jak tříd WinInet práce, naleznete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

Tato členská funkce je volána, když `CInternetConnection` je vytvořen objekt.

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>Parametry

*pSession*<br/>
Ukazatel [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objektu.

*pstrServer*<br/>
Ukazatel na řetězec obsahující název serveru.

*nPort*<br/>
Číslo, které identifikuje port Internet pro toto připojení.

*dwContext*<br/>
Identifikátor kontextu `CInternetConnection` objektu. Zobrazit **poznámky** Další informace o *dwContext*.

### <a name="remarks"></a>Poznámky

Nikdy neměl volat `CInternetConnection` sami; namísto toho zavolejte metodu [cinternetsession –](../../mfc/reference/cinternetsession-class.md) členskou funkci pro typ připojení, které chcete vytvořit:

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

Výchozí hodnota pro *dwContext* odesílají knihovny MFC pro `CInternetConnection`-odvozenému objektu z [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt vytvořený **InternetConnection**- odvozeného objektu. Výchozí hodnota je nastavená na 1; ale můžete explicitně přiřadit konkrétní kontextu identifikátoru v [cinternetsession –](../../mfc/reference/cinternetsession-class.md#cinternetsession) konstruktor pro připojení. Objekt a veškerou práci, kterou provádí bude spojená s ID tohoto kontextu. Identifikátor kontextu se vrátí do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytnout stav objektu, pomocí kterého je identifikován. Přečtěte si článek [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="getcontext"></a>  CInternetConnection::GetContext

Voláním této členské funkce k získání ID kontextu pro tuto relaci.

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>Návratová hodnota

ID aplikace přiřazené kontextu.

### <a name="remarks"></a>Poznámky

ID kontextu je původně určeno [cinternetsession –](../../mfc/reference/cinternetsession-class.md) a rozšíří na `CInternetConnection`– a [cinternetfile –](../../mfc/reference/cinternetfile-class.md)-odvozené třídy, pokud není uvedeno jinak ve volání funkce, které se otevře připojení. ID kontextu je spojen s jakoukoli operaci daného objektu a určuje informace o stavu operace vracené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

Další informace o tom, `GetContext` funguje s jinými třídami WinInet poskytnout informace o stavu uživatele najdete v článku [Internet první kroky: WinInet](../../mfc/wininet-basics.md) Další informace o identifikátor kontextu.

##  <a name="getservername"></a>  CInternetConnection::GetServerName

Voláním této členské funkce a získat tak název serveru přidružené k připojení k Internetu.

```
CString GetServerName() const;
```

### <a name="return-value"></a>Návratová hodnota

Název serveru, s nímž pracuje tento objekt připojení.

##  <a name="getsession"></a>  CInternetConnection::GetSession

Voláním této členské funkce, chcete-li získat ukazatel `CInternetSession` objekt, který je spojený s tímto připojením.

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel [cinternetsession –](../../mfc/reference/cinternetsession-class.md) objekt asociovaném s tímto objektem internetové připojení.

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

Tento operátor se získat popisovač úroveň rozhraní API pro aktuální relaci Internet.

```
operator HINTERNET() const;
```

## <a name="see-also"></a>Viz také:

[CObject – třída](../../mfc/reference/cobject-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)
