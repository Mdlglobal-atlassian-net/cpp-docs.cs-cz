---
title: CInternetException Class
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
ms.openlocfilehash: dedf8926f02dd36dc8d6ac8ab5ff4056b60dfc91
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270255"
---
# <a name="cinternetexception-class"></a>CInternetException Class

Představuje podmínku výjimky vztahující se k Internetu operaci.

## <a name="syntax"></a>Syntaxe

```
class CInternetException : public CException
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CInternetException::CInternetException](#cinternetexception)|Vytvoří `CInternetException` objektu.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CInternetException::m_dwContext](#m_dwcontext)|Hodnota kontextu přidružené operaci, která způsobila výjimku.|
|[CInternetException::m_dwError](#m_dwerror)|Chyba, která způsobila výjimku.|

## <a name="remarks"></a>Poznámky

`CInternetException` Třída zahrnuje dvě veřejné datové členy: jeden obsahuje kód chyby související s výjimkou a druhý obsahuje identifikátor kontextu Internetové aplikace přidružené k chybě.

Další informace o kontextu identifikátory pro aplikace, najdete v článku [Internet programování pomocí rozhraní WinInet](../../mfc/win32-internet-extensions-wininet.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[Cexception –](../../mfc/reference/cexception-class.md)

`CInternetException`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxinet.h

##  <a name="cinternetexception"></a>  CInternetException::CInternetException

Tato členská funkce je volána, když `CInternetException` je vytvořen objekt.

```
CInternetException(DWORD dwError);
```

### <a name="parameters"></a>Parametry

*dwError*<br/>
Chyba, která způsobila výjimku.

### <a name="remarks"></a>Poznámky

Vyvolání cinternetexception – volání globální funkce MFC [afxthrowinternetexception –](internet-url-parsing-globals.md#afxthrowinternetexception).

##  <a name="m_dwcontext"></a>  CInternetException::m_dwContext

Kontext hodnotu přidruženou k související operaci na Internetu.

```
DWORD_PTR m_dwContext;
```

### <a name="remarks"></a>Poznámky

Identifikátor kontextu je původně určeno [cinternetsession –](../../mfc/reference/cinternetsession-class.md) a předávány knihovny MFC pro [cinternetconnection –](../../mfc/reference/cinternetconnection-class.md)– a [cinternetfile –](../../mfc/reference/cinternetfile-class.md)-odvozené třídy. Můžete přepsat toto výchozí nastavení a přiřazení některého *dwContext* parametr hodnotu podle vašeho výběru. *dwContext* souvisí s jakoukoli operaci daného objektu. *dwContext* identifikuje informace o stavu operace vracené [CInternetSession::OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback).

##  <a name="m_dwerror"></a>  CInternetException::m_dwError

Chyba, která způsobila výjimku.

```
DWORD m_dwError;
```

### <a name="remarks"></a>Poznámky

Tato hodnota chyba může být systém kód chyby v nezdařila. H nebo chybovou hodnotu z rozhraní WININET. H.

Seznam kódy chyb systému Win32 naleznete v tématu [kódy chyb](/windows/desktop/Debug/system-error-codes). Seznam Internet specifické chybové zprávy najdete v tématu. Obě témata jsou v sadě Windows SDK.

## <a name="see-also"></a>Viz také:

[CException – třída](../../mfc/reference/cexception-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CException – třída](../../mfc/reference/cexception-class.md)
