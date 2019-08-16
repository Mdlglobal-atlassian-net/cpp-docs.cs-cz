---
title: CInternetException – třída
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
ms.openlocfilehash: c4f4c7a5b7594270aff9dfbc224e9a66ba09be3f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505910"
---
# <a name="cinternetexception-class"></a>CInternetException – třída

Představuje podmínku výjimky vztahující se k internetové operaci.

## <a name="syntax"></a>Syntaxe

```
class CInternetException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|`CInternetException` Vytvoří objekt.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Hodnota kontextu přidružená k operaci, která způsobila výjimku.|
|[CInternetException::m_dwError](#m_dwerror)|Chyba, která způsobila výjimku.|

## <a name="remarks"></a>Poznámky

`CInternetException` Třída obsahuje dva veřejné datové členy: jeden obsahuje kód chyby spojený s výjimkou a druhý obsahuje identifikátor kontextu internetové aplikace přidružené k chybě.

Další informace o identifikátorech kontextu pro internetové aplikace najdete v článku [internetové programování s](../../mfc/win32-internet-extensions-wininet.md)rozhraním Wininet.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CException –](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet. h

##  <a name="cinternetexception"></a>CInternetException::CInternetException

Tato členská funkce se volá, `CInternetException` když se vytvoří objekt.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Chcete-li vyvolat CInternetException, zavolejte globální funkci [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)knihovny MFC.

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

Hodnota kontextu přidružená k související internetové operaci.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Poznámky

Identifikátor kontextu je původně zadán v [CInternetSession](../../mfc/reference/cinternetsession-class.md) a PŘEdaný knihovnou MFC na třídy odvozené z [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)a [CInternetFile](../../mfc/reference/cinternetfile-class.md). Můžete přepsat toto výchozí nastavení a přiřadit libovolnému parametru *dwContext* hodnotu, kterou zvolíte. *dwContext* je přidružen k jakékoli operaci daného objektu. *dwContext* identifikuje informace o stavu operace vrácené funkcí [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

Chyba, která způsobila výjimku.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Poznámky

Tato chybová hodnota může být kód chyby systému, který se nachází v WINERROR. H nebo chybová hodnota z WININET. Y.

Seznam kódů chyb Win32 najdete v tématu [kódy chyb](/windows/win32/Debug/system-error-codes). Seznam chybových zpráv specifických pro Internet naleznete v tématu. Obě témata jsou v Windows SDK.

## <a name="see-also"></a>Viz také:

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
