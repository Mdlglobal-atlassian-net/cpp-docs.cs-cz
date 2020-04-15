---
title: Třída CInternetException
ms.date: 11/04/2016
f1_keywords:
- CInternetException
- AFXINET/CInternetException
- AFXINET/CInternetException::CInternetException
- AFXINET/CInternetException::m_dwContext
- AFXINET/CInternetException::m_dwError
helpviewer_keywords:
- CInternetException [MFC], CInternetException
- CInternetException [MFC], m_dwContext
- CInternetException [MFC], m_dwError
ms.assetid: 44fb3cbe-523e-4754-8843-a77909990b14
ms.openlocfilehash: b0239afa2b984ccf93d661ec11f11013c89fd912
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372410"
---
# <a name="cinternetexception-class"></a>Třída CInternetException

Představuje podmínku výjimky související s internetovou operací.

## <a name="syntax"></a>Syntaxe

```
class CInternetException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Vytvoří `CInternetException` objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Hodnota kontextu přidružená k operaci, která způsobila výjimku.|
|[CInternetException::m_dwError](#m_dwerror)|Chyba, která způsobila výjimku.|

## <a name="remarks"></a>Poznámky

Třída `CInternetException` obsahuje dva členy veřejných dat: jeden obsahuje kód chyby přidružený k výjimce a druhý obsahuje identifikátor kontextu internetové aplikace přidružené k chybě.

Další informace o kontextových identifikátorech internetových aplikací naleznete v článku [Internetové programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

## <a name="cinternetexceptioncinternetexception"></a><a name="cinternetexception"></a>CInternetException::CInternetException

Tato členská funkce `CInternetException` je volána při vytvoření objektu.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*chyba dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Chcete-li vyvolat CInternetException, volejte globální funkci knihovny MFC [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception).

## <a name="cinternetexceptionm_dwcontext"></a><a name="m_dwcontext"></a>CInternetException::m_dwContext

Hodnota kontextu přidružená k související internetové operaci.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Poznámky

Identifikátor kontextu je původně zadán v [cinternetsession](../../mfc/reference/cinternetsession-class.md) a předán knihovnou MFC na [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)- a [CInternetFile](../../mfc/reference/cinternetfile-class.md)-odvozené třídy. Můžete přepsat toto výchozí a přiřadit libovolný parametr *dwContext* hodnotu podle vašeho výběru. *dwContext* je spojena s jakoukoli operací daného objektu. *dwContext* identifikuje informace o stavu operace vrácené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

## <a name="cinternetexceptionm_dwerror"></a><a name="m_dwerror"></a>CInternetException::m_dwError

Chyba, která způsobila výjimku.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Poznámky

Tato chybová hodnota může být kód systémové chyby, který byl nalezen ve winerror. H nebo chybová hodnota z WININET. H.

Seznam kódů chyb win32 naleznete v [tématu Chybové kódy](/windows/win32/Debug/system-error-codes). Seznam chybových zpráv specifických pro Internet naleznete v tématu . Obě témata jsou v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
