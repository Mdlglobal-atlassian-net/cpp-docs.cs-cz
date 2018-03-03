---
title: "Třída CInternetConnection | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
dev_langs:
- C++
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0c20cee097ae0ba61a9106da0476541e7d7c18e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cinternetconnection-class"></a>CInternetConnection – třída
Spravuje připojení k internetového serveru.  
  
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
|[CInternetConnection::GetSession](#getsession)|Získá odkazy [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt přidružený k připojení.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|Popisovač pro relaci Internet.|  
  
## <a name="remarks"></a>Poznámky  
 Je základní třída pro třídy MFC [CFtpConnection](../../mfc/reference/cftpconnection-class.md), [CHttpConnection](../../mfc/reference/chttpconnection-class.md), a [CGopherConnection](../../mfc/reference/cgopherconnection-class.md). Každá z těchto tříd pro komunikaci s na příslušný server FTP, HTTP nebo gopher poskytuje další funkce.  
  
 K přímé komunikaci se serverem v Internetu, musíte mít [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu a `CInternetConnection` objektu.  
  
 Další informace o způsobu WinInet třídy pracovní, najdete v článku [Internet programování s WinInet](../../mfc/win32-internet-extensions-wininet.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetConnection`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxinet.h  
  
##  <a name="cinternetconnection"></a>CInternetConnection::CInternetConnection  
 Tento člen funkce je volána, když `CInternetConnection` je vytvořen objekt.  
  
```  
CInternetConnection(
    CInternetSession* pSession,  
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    DWORD_PTR dwContext = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `pSession`  
 Ukazatel [CInternetSession](../../mfc/reference/cinternetsession-class.md) objektu.  
  
 `pstrServer`  
 Ukazatel na řetězec obsahující název serveru.  
  
 `nPort`  
 Číslo, které identifikuje port Internetu pro toto připojení.  
  
 `dwContext`  
 Identifikátor kontext pro `CInternetConnection` objektu. V tématu **poznámky** Další informace o `dwContext`.  
  
### <a name="remarks"></a>Poznámky  
 Nikdy volat `CInternetConnection` sami; místo toho zavolejte [CInternetSession](../../mfc/reference/cinternetsession-class.md) – členská funkce pro typ připojení, které chcete vytvořit:  
  
- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)  
  
- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)  
  
- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)  
  
 Výchozí hodnota pro `dwContext` odesílají MFC k `CInternetConnection`-odvozeného od objektu [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt vytvořený **InternetConnection**-odvozené objektu. Ve výchozím nastavení je 1; však můžete explicitně přiřadit konkrétní kontext identifikátor v [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession) konstruktor pro připojení. Objekt a všechny práce, kterou dělá bude spojený s ID tohoto kontextu. Identifikátor kontextu je vrácen do [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback) poskytovat stav na objekt, ke kterému se identifikuje. Najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="getcontext"></a>CInternetConnection::GetContext  
 Volání této funkce člen získat ID kontextu pro tuto relaci.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 ID aplikace přiřazené kontextu.  
  
### <a name="remarks"></a>Poznámky  
 ID kontextu je byl původně specifikován v [CInternetSession](../../mfc/reference/cinternetsession-class.md) a rozšiřuje na `CInternetConnection`- a [CInternetFile](../../mfc/reference/cinternetfile-class.md)-odvozené třídy, pokud není uvedeno jinak ve volání funkce, které se otevře připojení. ID kontextu je přidružen všechny operace daného objektu a identifikuje vrácené informace o stavu operace [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).  
  
 Další informace o tom, **getcontext –** funguje s jinými WinInet třídami poskytnout informace o stavu uživatele, najdete v článku [první kroky Internet: WinInet](../../mfc/wininet-basics.md) Další informace o kontextu identifikátor.  
  
##  <a name="getservername"></a>CInternetConnection::GetServerName  
 Volání této funkce člen získat název serveru přidružené k připojení k Internetu.  
  
```  
CString GetServerName() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Název serveru, který tento objekt připojení ve spolupráci s.  
  
##  <a name="getsession"></a>CInternetConnection::GetSession  
 Volání této funkce člen získat ukazatel `CInternetSession` objekt, který je spojen s tímto připojením.  
  
```  
CInternetSession* GetSession() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel [CInternetSession](../../mfc/reference/cinternetsession-class.md) objekt přidružené k tomuto objektu internetové připojení.  
  
##  <a name="operator_hinternet"></a>CInternetConnection::operator HINTERNET  
 Operátor se získat popisovač úroveň rozhraní API pro aktuální relaci Internet.  
  
```  
operator HINTERNET() const;  
```  
  
## <a name="see-also"></a>Viz také  
 [CObject – třída](../../mfc/reference/cobject-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)



