---
title: Isupporterrorinfoimpl – třída
ms.date: 11/04/2016
f1_keywords:
- ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl
- ATLCOM/ATL::ISupportErrorInfoImpl::InterfaceSupportsErrorInfo
helpviewer_keywords:
- ISupportErrorInfo ATL implementation
- ISupportErrorInfoImpl class
- error information, ATL
ms.assetid: e33a4b11-a123-41cf-bcea-7b19743902af
ms.openlocfilehash: f7e300e30ff0f14b56d2a1bae86b00e090674679
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274760"
---
# <a name="isupporterrorinfoimpl-class"></a>Isupporterrorinfoimpl – třída

Tato třída poskytuje výchozí implementaci třídy [ISupportErrorInfo rozhraní](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) a můžou používat, když pouze jedno rozhraní vygeneruje chyby na objekt.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<const IID* piid>
class ATL_NO_VTABLE ISupportErrorInfoImpl
   : public ISupportErrorInfo
```

#### <a name="parameters"></a>Parametry

*piid*<br/>
Ukazatel na IID rozhraní, které podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo).

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[ISupportErrorInfoImpl::InterfaceSupportsErrorInfo](#interfacesupportserrorinfo)|Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) rozhraní.|

## <a name="remarks"></a>Poznámky

[ISupportErrorInfo rozhraní](/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo) zajistí, že informace o chybě můžou být vrácen do klienta. Objekty, které používají `IErrorInfo` musí implementovat `ISupportErrorInfo`.

Třída `ISupportErrorInfoImpl` poskytuje výchozí implementaci třídy `ISupportErrorInfo` a můžou používat, když pouze jedno rozhraní vygeneruje chyby na objekt. Příklad:

[!code-cpp[NVC_ATL_COM#48](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_1.h)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ISupportErrorInfo`

`ISupportErrorInfoImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="interfacesupportserrorinfo"></a>  ISupportErrorInfoImpl::InterfaceSupportsErrorInfo

Určuje, zda rozhraní identifikovaný `riid` podporuje [IErrorInfo](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) rozhraní.

```
STDMETHOD(InterfaceSupportsErrorInfo)(REFIID riid);
```

### <a name="remarks"></a>Poznámky

Zobrazit [ISupportErrorInfo::InterfaceSupportsErrorInfo](/windows/desktop/api/oaidl/nf-oaidl-isupporterrorinfo-interfacesupportserrorinfo) ve Windows SDK.

##  <a name="getsize"></a>  IThreadPoolConfig::GetSize

Volejte tuto metodu za účelem získání počet vláken ve fondu.

```
STDMETHOD(GetSize)(int* pnNumThreads);
```

### <a name="parameters"></a>Parametry

*pnNumThreads*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží počet vláken ve fondu.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

[!code-cpp[NVC_ATL_Utilities#134](../../atl/codesnippet/cpp/isupporterrorinfoimpl-class_2.cpp)]

##  <a name="gettimeout"></a>  IThreadPoolConfig::GetTimeout

Volejte tuto metodu za účelem získání maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
STDMETHOD(GetTimeout)(DWORD* pdwMaxWait);
```

### <a name="parameters"></a>Parametry

*pdwMaxWait*<br/>
[out] Adresa proměnné, která v případě úspěchu, obdrží maximální dobu v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

##  <a name="setsize"></a>  IThreadPoolConfig::SetSize

Voláním této metody nastavte počet vláken ve fondu.

```
STDMETHOD(SetSize)int nNumThreads);
```

### <a name="parameters"></a>Parametry

*nNumThreads*<br/>
Požadovaný počet vláken ve fondu.

Pokud *nNumThreads* je záporný, jeho absolutní hodnota se vynásobí číslo odpovídající počtu procesorů v počítači, chcete-li získat celkový počet vláken.

Pokud *nNumThreads* je nula, ATLS_DEFAULT_THREADSPERPROC bude vynásobené celkovým počtem procesorů v počítači, chcete-li získat celkový počet vláken.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

##  <a name="settimeout"></a>  IThreadPoolConfig::SetTimeout

Volejte tuto metodu za účelem nastavení maximální doby v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

```
STDMETHOD(SetTimeout)(DWORD dwMaxWait);
```

### <a name="parameters"></a>Parametry

*dwMaxWait*<br/>
Maximální požadovaný čas v milisekundách, fondu vláken bude čekání na vlákno pro vypnutí.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="example"></a>Příklad

Zobrazit [IThreadPoolConfig::GetSize](#getsize).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
